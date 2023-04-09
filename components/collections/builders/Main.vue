<template>
  <div>
    <div>
      <CollectionsBuildersList
        @openAddSidebar="openAddSidebar"
        @editBuilder="editBuilder"
        @deleteBuilder="deleteBuilder"
        :builderData="builderData"
      />
    </div>
    <div v-if="showSideBar" :key="renderAdd">
      <CollectionsBuildersAdd @addBuilder="addBuilder" />
    </div>
    <div v-if="showEditSidebar">
      <CollectionsBuildersEdit
        @updateBuilder="updateBuilder"
        :editBuilderData="editBuilderData"
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
const builderData = ref([]);

const editBuilderData = ref({});

const openAddSidebar = () => {
  showSideBar.value = true;
  renderAdd.value++;
};

const editBuilder = (data: object) => {
  editBuilderData.value = { ...data };
  showEditSidebar.value = true;
  renderEdit.value++;
};

const getBuildersDetails = async () => {
const { data: getBuildersData } = await useAuthLazyFetch(
  `https://v1-orm-gharpe.mercury.infinity-api.net/api/builder/?offset=0&limit=100&sort_column=id&sort_direction=desc`
);
builderData.value = getBuildersData.value;
}
getBuildersDetails();

const addBuilder = async (data: Object) => {
  const postOptions = {
    body: data,
  };
  await useAuthLazyFetchPost(
    `https://v1-orm-gharpe.mercury.infinity-api.net/api/builder/`,
    postOptions
  );
  getBuildersDetails();
  builderData.value.unshift(data);
};

const updateBuilder = async (body: Object) => {
  const putOptions = {
    body: body,
  };
  await useAuthLazyFetchPut(
    `https://v1-orm-gharpe.mercury.infinity-api.net/api/builder/${body.uid}`,
    putOptions
  );
  const { data: response } = await useAuthLazyFetch(
    `https://v1-orm-gharpe.mercury.infinity-api.net/api/builder/?offset=0&limit=100&sort_column=id&sort_direction=desc`
  );
  builderData.value = response.value;
};

const deleteBuilder = async (data: object, index: number) => {
  await useAuthLazyFetchDelete(
    `https://v1-orm-gharpe.mercury.infinity-api.net/api/builder/${data.uid}`
  );
  builderData.value.splice(index, 1);
};
</script>