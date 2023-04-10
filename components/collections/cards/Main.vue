<template>
  <div>
    <CollectionsCardsList
      @openAddContact="openAddContact"
      @editContactData="editContactData"
      @deleteContact="deleteContact"
      :getContacts="contacts"
    />
    <CollectionsCardsAdd
      v-if="openModal"
      :key="renderAdd"
      @addContact="addContact"
    />
    <CollectionsCardsEdit
      v-if="openEditModal"
      :key="renderEdit"
      @updateContact="updateContact"
      :editContact="editContact"
    />
  </div>
</template>
<script setup lang="ts">
import { ref, onMounted } from "vue";

const openModal = ref(false);
const openEditModal = ref(false);
const renderAdd = ref(0);
const renderEdit = ref(0);
const contacts = ref([]);
const editContact = ref({});

const openAddContact = () => {
  openModal.value = true;
  renderAdd.value++;
};

const addContact = (data: any) => {
    console.log("data",data)
  contacts.value.push(data);
  localStorage.setItem("contacts", JSON.stringify(contacts.value));
};

const editContactData = (data: object) => {
  editContact.value = { ...data };
  openEditModal.value = true;
  renderEdit.value++;
};

const updateContact = (data: object) => {
  //contacts.value.push(data);
  localStorage.setItem("contacts", JSON.stringify(contacts.value));
};

onMounted(() => {
  const getContacts = localStorage.getItem("contacts");
  contacts.value = JSON.parse(getContacts);
});

const deleteContact = (index: number) => {
    contacts.value.splice(index, 1);
    localStorage.setItem("contacts", JSON.stringify(contacts.value))

}
</script>