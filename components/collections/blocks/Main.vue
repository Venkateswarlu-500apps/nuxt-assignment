<template>
  <div>
    <CollectionsBlocksList
      @openAddBlocks="openAddBlocks"
      @editBlocks="editBlocks"
      @deleteBlocks="deleteBlocks"
      :getBolcksData="blocksData"
    />
    <CollectionsBlocksAdd
      v-if="showAddBlock"
      @saveBlocks="saveBlocks"
      :key="renderAdd"
    />
    <CollectionsBlocksEdit
      v-if="showEditBlock"
      @updateBlocks="updateBlocks"
      :editBlocksData="editBlocksData"
      :key="renderEdit"
    />
  </div>
</template>
<script setup lang="ts">
const showAddBlock = ref(false);
const showEditBlock = ref(false);
const renderAdd = ref(0);
const renderEdit = ref(0);
const blocksData = ref([]);
const editBlocksData = ref({});

const openAddBlocks = () => {
  showAddBlock.value = true;
  renderAdd.value++;
};

const editBlocks = (data: object) => {
  showEditBlock.value = true;
  renderEdit.value++;
  editBlocksData.value = {...data};
};

const { data: getBlocks } = await useAuthLazyFetch(
  `https://v1-orm-lib.mars.hipso.cc/api/blocks/?offset=0&limit=100&sort_column=id&sort_direction=desc`
);
blocksData.value = getBlocks.value;

const saveBlocks = async (data: object) => {
  const saveOptions = {
    body: data,
  };
  await useAuthLazyFetchPost(
    `https://v1-orm-lib.mars.hipso.cc/api/blocks/
`,
    saveOptions
  );
  blocksData.value.unshift(data);
};

const updateBlocks = async (data: object) => {
  const updateOptions = {
    body: data,
  };
  await useAuthLazyFetchPut(
    `https://v1-orm-lib.mars.hipso.cc/api/blocks/${data.uid}`,
    updateOptions
  );
  const { data: response } = await useAuthLazyFetch(
    "https://v1-orm-lib.mars.hipso.cc/api/blocks/?offset=0&limit=100&sort_column=id&sort_direction=desc"
  );
  blocksData.value = response.value;
};

const deleteBlocks = async (data: object, index: number) => {
  await useAuthLazyFetchDelete(
    `https://v1-orm-lib.mars.hipso.cc/api/blocks/${data.uid}`
  );
  blocksData.value.splice(index, 1);
};
</script>