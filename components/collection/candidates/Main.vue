<template>
  <div>
    <div>
    <CollectionsCandidatesList
      @openSidebar="openSidebar"
      :candidatesData="candidatesData"
    /></div>
<div  v-if="showSidebar">
    <CollectionsCandidatesAdd
       :key="renderAdd"
      @addCandidateData="addCandidate"
    /></div>
  </div>
</template>
  <script setup lang="ts">
import { ref } from "vue";
const showSidebar = ref(false);
const renderAdd =ref(0)

const openSidebar = () => {
  showSidebar.value = true;
  renderAdd.value++
};

const addCandidate = (data: object, show: boolean) => {
  const postOptions = {
    method: "POST",
    headers: {
      "Content-Type": "application/json",
      Authorization: `Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1IjoiYzI4OGRlNzBjYWYyNDUxODk4ZDRhMGM2N2U0ZmVkZDIiLCJkIjoiMTY4MDA4OSIsInIiOiJzYSIsInAiOiJmcmVlIiwiYSI6ImZpbmRlci5pbyIsImwiOiJ1czEiLCJleHAiOjE2ODMyODExOTV9.gl7Z_P_zA3fGoIH9mulaZF4tcA2vvln4x_dremExFIo`,
    },
    body: JSON.stringify(data),
  };

  const addCandidateData = useAuthLazyFetchPost(
    "https://v7-stark-db-orm.mercury.infinity-api.net/api/mock-interviews/",
    postOptions
  );
  candidatesData.value.unshift(data)
};

const getOptions = {
  method: "GET",
  headers: {
    "Content-Type": "application/json",
    Authorization: `Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1IjoiYzI4OGRlNzBjYWYyNDUxODk4ZDRhMGM2N2U0ZmVkZDIiLCJkIjoiMTY4MDA4OSIsInIiOiJzYSIsInAiOiJmcmVlIiwiYSI6ImZpbmRlci5pbyIsImwiOiJ1czEiLCJleHAiOjE2ODMyODExOTV9.gl7Z_P_zA3fGoIH9mulaZF4tcA2vvln4x_dremExFIo`,
  },
};
var getData = await useAuthLazyFetch(
  "https://v7-stark-db-orm.mercury.infinity-api.net/api/mock-interviews/?offset=0&limit=100&sort_column=id&sort_direction=desc",
  getOptions
);

let candidatesData = ref(getData.data._rawValue)

</script>