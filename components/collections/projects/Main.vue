<template>
  <div>
    <div>
      <CollectionsProjectsList
        @openSidebar="openSidebar"
        :projectData="projectData"
        @deleteProject="deleteProject"
        @editProject="editProject"
      />
    </div>
    <div v-if="showSideBar" :key="renderAdd">
      <CollectionsProjectsAdd @addProject="addProject" />
    </div>
    <div v-if="showEditSidebar">
      <CollectionsProjectsEdit
        @updateProject="updateProject"
        :projectsData="editData"
        :key="renderEdit"
      />
    </div>
  </div>
</template>
  
  <script setup lang="ts">
import { ref } from "vue";
const showSideBar = ref(false);
const showEditSidebar = ref(false);
const renderAdd = ref(0);
const renderEdit = ref(0);
const editData = ref({});
let editIndex = ref();

const openSidebar = () => {
  showSideBar.value = true;
  renderAdd.value++;
};

const editProject = (data: object, index: number) => {
  editData.value = data;
  editIndex.value = index;
  showEditSidebar.value = true;
  renderEdit.value++;
};
const addProject = (data: Object) => {
  const postOptions = {
    method: "POST",
    headers: {
      "Content-Type": "application/json",
      Authorization: `Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1IjoiYzI4OGRlNzBjYWYyNDUxODk4ZDRhMGM2N2U0ZmVkZDIiLCJkIjoiMTY4MDA4OSIsInIiOiJzYSIsInAiOiJmcmVlIiwiYSI6ImZpbmRlci5pbyIsImwiOiJ1czEiLCJleHAiOjE2ODMyODExOTV9.gl7Z_P_zA3fGoIH9mulaZF4tcA2vvln4x_dremExFIo`,
    },
    body: data,
  };
  const addProjectData = useAuthLazyFetchPost(
    `https://v1-orm-gharpe.mercury.infinity-api.net/api/projects/`,
    postOptions
  );
  projectData.value.unshift(data);
};

const getProjects = {
  method: "GET",
  headers: {
    "Content-Type": "application/json",
    Authorization: `Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1IjoiYzI4OGRlNzBjYWYyNDUxODk4ZDRhMGM2N2U0ZmVkZDIiLCJkIjoiMTY4MDA4OSIsInIiOiJzYSIsInAiOiJmcmVlIiwiYSI6ImZpbmRlci5pbyIsImwiOiJ1czEiLCJleHAiOjE2ODMyODExOTV9.gl7Z_P_zA3fGoIH9mulaZF4tcA2vvln4x_dremExFIo`,
  }
};

const getProjectsData = useAuthLazyFetch(
  `https://v1-orm-gharpe.mercury.infinity-api.net/api/projects/`
);

const updateProject = (body: Object) => {
  const putOptions = {
    method: "PUT",
    headers: {
      "Content-Type": "application/json",
      Authorization: `Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1IjoiYzI4OGRlNzBjYWYyNDUxODk4ZDRhMGM2N2U0ZmVkZDIiLCJkIjoiMTY4MDA4OSIsInIiOiJzYSIsInAiOiJmcmVlIiwiYSI6ImZpbmRlci5pbyIsImwiOiJ1czEiLCJleHAiOjE2ODMyODExOTV9.gl7Z_P_zA3fGoIH9mulaZF4tcA2vvln4x_dremExFIo`,
    },
    body: body,
  };
  const editData = useAuthLazyFetchPut(
    `https://v1-orm-gharpe.mercury.infinity-api.net/api/projects/${body.uid}`,
    putOptions
  );
};

const deleteProject = (data: object, index: number) => {
  const deleteOptions = {
    method: "DELETE",
    headers: {
      "Content-Type": "application/json",
      Authorization: `Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1IjoiYzI4OGRlNzBjYWYyNDUxODk4ZDRhMGM2N2U0ZmVkZDIiLCJkIjoiMTY4MDA4OSIsInIiOiJzYSIsInAiOiJmcmVlIiwiYSI6ImZpbmRlci5pbyIsImwiOiJ1czEiLCJleHAiOjE2ODMyODExOTV9.gl7Z_P_zA3fGoIH9mulaZF4tcA2vvln4x_dremExFIo`,
    },
  };
  const deleteProjectData = useAuthLazyFetchDelete(
    `https://v1-orm-gharpe.mercury.infinity-api.net/api/projects/${data.uid}`
  );
  projectData.value.splice(index, 1);
};

let projectData = ref(getProjectsData.data._rawValue);
</script>