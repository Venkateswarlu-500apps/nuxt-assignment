<template>
  <div>
    <CollectionsJobsList @openSidebar="openSidebar" :jobDetails="jobDetails"/>
    <CollectionsJobsAdd v-if="showSideBar" :key="render" @saveJob="addJob"/>
  </div>
</template>
<script setup lang="ts">
import { ref } from "vue";

const showSideBar = ref(false);
const render = ref(0);

const openSidebar = ()=>{
  showSideBar.value = true;
  render.value++;
}

const addJob = (data: object) => {
  const addOptions = {
    method: "POST",
    headers: {
      "Content-Type": "application/json",
      Authorization: `Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1IjoiYzI4OGRlNzBjYWYyNDUxODk4ZDRhMGM2N2U0ZmVkZDIiLCJkIjoiMTY4MDA4OSIsInIiOiJzYSIsInAiOiJmcmVlIiwiYSI6ImZpbmRlci5pbyIsImwiOiJ1czEiLCJleHAiOjE2ODMyODExOTV9.gl7Z_P_zA3fGoIH9mulaZF4tcA2vvln4x_dremExFIo`,
    },
    body: JSON.stringify(data),
  };

  const addJobData = useAuthLazyFetchPost(
    "https://v7-stark-db-orm.mercury.infinity-api.net/api/jobs/",
    addOptions
  );
  jobDetails.value.unshift(data)
};

const getJob = {
  method: "GET",
  headers: {
    "Content-Type": "application/json",
    Authorization: `Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1IjoiYzI4OGRlNzBjYWYyNDUxODk4ZDRhMGM2N2U0ZmVkZDIiLCJkIjoiMTY4MDA4OSIsInIiOiJzYSIsInAiOiJmcmVlIiwiYSI6ImZpbmRlci5pbyIsImwiOiJ1czEiLCJleHAiOjE2ODMyODExOTV9.gl7Z_P_zA3fGoIH9mulaZF4tcA2vvln4x_dremExFIo`,
  }
};
var getJobDetails = await useAuthLazyFetch(
  "https://v7-stark-db-orm.mercury.infinity-api.net/api/jobs/?offset=0&limit=10&sort_column=id&sort_direction=desc",
  getJob
);

let jobDetails = ref(getJobDetails.data._rawValue)
</script>
