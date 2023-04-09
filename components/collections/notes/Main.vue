<template>
    <div>
      <CollectionsNotesList
        @openAddNotes="openAddNotes"
        @editNotes="editNotes"
        @deleteNotes="deleteNotes"
        :getNotesData="notesData"
      />
      <CollectionsNotesAdd
        v-if="showAddNote"
        @saveNotes="saveNotes"
        :key="renderAdd"
      />
      <CollectionsNotesEdit
        v-if="showEditNote"
        @updateNotes="updateNotes"
        :editNotesData="editNotesData"
        :key="renderEdit"
      />
    </div>
  </template>
  <script setup lang="ts">
  const showAddNote = ref(false);
  const showEditNote = ref(false);
  const renderAdd = ref(0);
  const renderEdit = ref(0);
  const notesData = ref([]);
  const editNotesData = ref({});
  
  const openAddNotes = () => {
    showAddNote.value = true;
    renderAdd.value++;
  };
  
  const editNotes = (data: object) => {
    showEditNote.value = true;
    renderEdit.value++;
    editNotesData.value = {...data};
  };
  
  const { data: getNotes } = await useAuthLazyFetch(
    `https://v1-orm-lib.mars.hipso.cc/api/notes/CONTACTS/22?project_id=16&offset=0&limit=100&sort_column=id&sort_direction=desc
`
  );
  notesData.value = getNotes.value;
  
  const saveNotes = async (data: object) => {
    const saveOptions = {
      body: data,
    };
    await useAuthLazyFetchPost(
      `https://v1-orm-lib.mars.hipso.cc/api/notes/CONTACTS/22
  `,
      saveOptions
    );
    notesData.value.unshift(data);
  };
  
  const updateNotes = async (data: object) => {
    const updateOptions = {
      body: data,
    };
    await useAuthLazyFetchPut(
      `https://v1-orm-lib.mars.hipso.cc/api/notes/${data.uid}`,
      updateOptions
    );
    const { data: response } = await useAuthLazyFetch(
      `https://v1-orm-lib.mars.hipso.cc/api/notes/CONTACTS/22?project_id=16&offset=0&limit=100&sort_column=id&sort_direction=desc`
    );
    notesData.value = response.value;
  };
  
  const deleteNotes = async (data: object, index: number) => {
    await useAuthLazyFetchDelete(
      `https://v1-orm-lib.mars.hipso.cc/api/notes/${data.uid}`
    );
    notesData.value.splice(index, 1);
  };
  </script>