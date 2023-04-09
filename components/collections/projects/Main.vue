<template>
  <div>
    <div>
      <CollectionsProjectsList @openSidebar="openSidebar" @editProject="editProject" @deleteProject="deleteProject"
        :projectData="projectData" />
    </div>
    <div v-if="showSideBar" :key="renderAdd">
      <CollectionsProjectsAdd @addProject="addProject" />
    </div>
    <div v-if="showEditSidebar">
      <CollectionsProjectsEdit @updateProject="updateProject" :editData="editData" :key="renderEdit" />
    </div>
  </div>
</template>
  
<script setup lang="ts">
import { ref } from "vue";
const showSideBar = ref(false);
const showEditSidebar = ref(false);
const renderAdd = ref(0);
const renderEdit = ref(0);
const projectData = ref([]);
const editData = ref({});

const openSidebar = () => {
  showSideBar.value = true;
  renderAdd.value++;
};

const editProject = (data: object) => {
  editData.value = { ...data };
  showEditSidebar.value = true;
  renderEdit.value++;
};
const getProjecsDetails = async () => {
  const { data: getProjectsData } = await useAuthLazyFetch(
    `https://v1-orm-gharpe.mercury.infinity-api.net/api/projects/`
  );
  projectData.value = getProjectsData.value;
};
getProjecsDetails();

const addProject = async (data: Object) => {
  const postOptions = {
    body: data,
  };
  await useAuthLazyFetchPost(
    `https://v1-orm-gharpe.mercury.infinity-api.net/api/projects/`,
    postOptions
  );
  getProjecsDetails();
};


const updateProject = async (body: Object) => {
  const putOptions = {
    body: body,
  };

  await useAuthLazyFetchPut(
    `https://v1-orm-gharpe.mercury.infinity-api.net/api/projects/${body.uid}`,
    putOptions
  );

  const { data: response } = await useAuthLazyFetch(
    `https://v1-orm-gharpe.mercury.infinity-api.net/api/projects/`
  );
  projectData.value = response.value;
};

const deleteProject = async (data: object, index: number) => {
  await useAuthLazyFetchDelete(
    `https://v1-orm-gharpe.mercury.infinity-api.net/api/projects/${data.uid}`
  );
  projectData.value.splice(index, 1);
};
</script>