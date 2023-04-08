<template>
    <div class="relative">
    <div class="px-4 sm:px-6 lg:px-8">
      <div class="sm:flex sm:items-center">
        <div class="sm:flex-auto"></div>
        <div class="mt-4 sm:ml-16 sm:mt-0 sm:flex-none">
            <button class="mt-6 px-3 py-2 text-center text-sm shadow-sm block bg-green-500 rounded-md text-white font-medium hover:bg-green-700 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600" type="button" @click="emit('openSidebar')">Add Jobs</button>
        </div>
      </div>
    <div class="mt-4 sm:ml-16 sm:mt-0 sm:flex-none">
        
    </div>
    <div class="mt-8 flow-root grid-rows-3 mx-auto my-5 border rounded-lg overflow-x-auto">
        <div class="-mx-4 -my-2 sm:-mx-6 lg:-mx-8">
          <div
            class="inline-block min-w-full py-2 align-middle sm:px-6 lg:px-8"
          >
            <table class="min-w-full divide-y divide-gray-300">
              <thead class="bg-gray-400">
                <tr>
                  <th 
                    scope="col"
                    class="py-3.5 pl-4 pr-3 text-center text-sm font-semibold text-gray-900 sm:pl-0"
                   
                  >
                  Title
                  </th>
                  <th 
                    scope="col"
                    class="py-3.5 pl-4 pr-3 text-center text-sm font-semibold text-gray-900 sm:pl-0"
                   
                  >
                  Industries
                  </th><th 
                    scope="col"
                    class="py-3.5 pl-4 pr-3 text-center text-sm font-semibold text-gray-900 sm:pl-0"
                   
                  >
                  Designation
                  </th><th 
                    scope="col"
                    class="py-3.5 pl-4 pr-3 text-center text-sm font-semibold text-gray-900 sm:pl-0"
                   
                  >
                  Education Qualification
                  </th><th 
                    scope="col"
                    class="py-3.5 pl-4 pr-3 text-center text-sm font-semibold text-gray-900 sm:pl-0"
                   
                  >
                  Skills Description
                  </th><th 
                    scope="col"
                    class="py-3.5 pl-4 pr-3 text-center text-sm font-semibold text-gray-900 sm:pl-0"
                   
                  >
                  External Source
                  </th><th 
                    scope="col"
                    class="py-3.5 pl-4 pr-3 text-center text-sm font-semibold text-gray-900 sm:pl-0"
                   
                  >
                  Experience Level
                  </th><th 
                    scope="col"
                    class="py-3.5 pl-4 pr-3 text-center text-sm font-semibold text-gray-900 sm:pl-0"
                   
                  >
                  Listed Date
                  </th><th 
                    scope="col"
                    class="py-3.5 pl-4 pr-3 text-center text-sm font-semibold text-gray-900 sm:pl-0"
                   
                  >
                  Description
                  </th><th 
                    scope="col"
                    class="py-3.5 pl-4 pr-3 text-center text-sm font-semibold text-gray-900 sm:pl-0"
                   
                  >
                  Experience In Place of Education
                  </th><th 
                    scope="col"
                    class="py-3.5 pl-4 pr-3 text-center text-sm font-semibold text-gray-900 sm:pl-0"
                   
                  >
                  Expiry Date
                  </th><th 
                    scope="col"
                    class="py-3.5 pl-4 pr-3 text-center text-sm font-semibold text-gray-900 sm:pl-0"
                   
                  >
                  Apply Url
                  </th><th 
                    scope="col"
                    class="py-3.5 pl-4 pr-3 text-center text-sm font-semibold text-gray-900 sm:pl-0"
                   
                  >
                  Operation Type
                  </th><th 
                    scope="col"
                    class="py-3.5 pl-4 pr-3 text-center text-sm font-semibold text-gray-900 sm:pl-0"
                   
                  >
                  Work Hours
                  </th><th 
                    scope="col"
                    class="py-3.5 pl-4 pr-3 text-center text-sm font-semibold text-gray-900 sm:pl-0"
                   
                  >
                  Working Days
                  </th><th 
                    scope="col"
                    class="py-3.5 pl-4 pr-3 text-center text-sm font-semibold text-gray-900 sm:pl-0"
                   
                  >
                  Work Remote Allowed
                  </th><th 
                    scope="col"
                    class="py-3.5 pl-4 pr-3 text-center text-sm font-semibold text-gray-900 sm:pl-0"
                   
                  >
                  Workplace Type
                  </th><th 
                    scope="col"
                    class="py-3.5 pl-4 pr-3 text-center text-sm font-semibold text-gray-900 sm:pl-0"
                   
                  >
                  Employment Status
                  </th><th 
                    scope="col"
                    class="py-3.5 pl-4 pr-3 text-center text-sm font-semibold text-gray-900 sm:pl-0"
                   
                  >
                  Company Job Code
                  </th><th 
                    scope="col"
                    class="py-3.5 pl-4 pr-3 text-center text-sm font-semibold text-gray-900 sm:pl-0"
                   
                  >
                  State
                  </th><th 
                    scope="col"
                    class="py-3.5 pl-4 pr-3 text-center text-sm font-semibold text-gray-900 sm:pl-0"
                   
                  >
                  Job Count
                  </th><th 
                    scope="col"
                    class="py-3.5 pl-4 pr-3 text-center text-sm font-semibold text-gray-900 sm:pl-0"
                   
                  >
                  Gender
                  </th><th 
                    scope="col"
                    class="py-3.5 pl-4 pr-3 text-center text-sm font-semibold text-gray-900 sm:pl-0"
                   
                  >
                  Languages
                  </th><th 
                    scope="col"
                    class="py-3.5 pl-4 pr-3 text-center text-sm font-semibold text-gray-900 sm:pl-0"
                   
                  >
                  Start Date
                  </th><th 
                    scope="col"
                    class="py-3.5 pl-4 pr-3 text-center text-sm font-semibold text-gray-900 sm:pl-0"
                   
                  >
                  Job Benefits
                  </th><th 
                    scope="col"
                    class="py-3.5 pl-4 pr-3 text-center text-sm font-semibold text-gray-900 sm:pl-0"
                   
                  >
                  Show Poster
                  </th><th 
                    scope="col"
                    class="py-3.5 pl-4 pr-3 text-center text-sm font-semibold text-gray-900 sm:pl-0"
                   
                  >
                  Poster Info
                  </th><th 
                    scope="col"
                    class="py-3.5 pl-4 pr-3 text-center text-sm font-semibold text-gray-900 sm:pl-0"
                   
                  >
                  Listing Type
                  </th><th 
                    scope="col"
                    class="py-3.5 pl-4 pr-3 text-center text-sm font-semibold text-gray-900 sm:pl-0"
                   
                  >
                  Last Scrapped Date
                  </th><th 
                    scope="col"
                    class="py-3.5 pl-4 pr-3 text-center text-sm font-semibold text-gray-900 sm:pl-0"
                   
                  >
                  Draft
                  </th>
                </tr>
              </thead>
              <tbody class="divide-y divide-gray-200">
                <tr
                  v-for="(data, index) in jobDetails"
                  :key="index"
                >
                  <td
                    class="uppercase whitespace-nowrap py-4 pl-4 pr-3 text-sm text-center font-medium text-gray-900 sm:pl-0"
                  >
                    {{ data.title }}
                  </td>
                  <td
                    class="uppercase whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-gray-900 sm:pl-0"
                  >
                    {{ data.industries }}
                  </td>
                  <td
                    class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-gray-900 sm:pl-0"
                  >
                    {{ data.designation }}
                  </td>
                  <td
                    class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-gray-900 sm:pl-0"
                  >
                    {{ data.education_qualification }}
                  </td>
                  <td
                    class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-gray-900 sm:pl-0"
                  >
                    {{ data.skills_description }}
                  </td>

                  <td
                    class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-gray-900 sm:pl-0"
                  >
                    {{ data.external_source }}
                  </td>
                  <td
                    class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-gray-900 sm:pl-0"
                  >
                    {{ data.experience_level }}
                  </td>
                  <td
                    class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-gray-900 sm:pl-0"
                  >
                    {{ data.listed_date }}
                  </td>
                  <td
                    class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-gray-900 sm:pl-0"
                  >
                    {{ data.description }}
                  </td> <td
                    class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-gray-900 sm:pl-0"
                  >
                    {{ data.experience_in_placeof_education }}
                  </td> <td
                    class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-gray-900 sm:pl-0"
                  >
                    {{ data.expiry_date }}
                  </td> <td
                    class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-gray-900 sm:pl-0"
                  >
                    {{ data.apply_url }}
                  </td> <td
                    class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-gray-900 sm:pl-0"
                  >
                    {{ data.operation_type }}
                  </td> <td
                    class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-gray-900 sm:pl-0"
                  >
                    {{ data.work_hours }}
                  </td> <td
                    class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-gray-900 sm:pl-0"
                  >
                    {{ data.working_days }}
                  </td> <td
                    class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-gray-900 sm:pl-0"
                  >
                    {{ data.is_work_remote_allowed }}
                  </td> <td
                    class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-gray-900 sm:pl-0"
                  >
                    {{ data.workplace_type }}
                  </td> <td
                    class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-gray-900 sm:pl-0"
                  >
                    {{ data.employment_status }}
                  </td> <td
                    class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-gray-900 sm:pl-0"
                  >
                    {{ data.company_job_code }}
                  </td> <td
                    class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-gray-900 sm:pl-0"
                  >
                    {{ data.state }}
                  </td> <td
                    class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-gray-900 sm:pl-0"
                  >
                    {{ data.job_count }}
                  </td> <td
                    class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-gray-900 sm:pl-0"
                  >
                    {{ data.gender }}
                  </td> <td
                    class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-gray-900 sm:pl-0"
                  >
                    {{ data.languages }}
                  </td> <td
                    class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-gray-900 sm:pl-0"
                  >
                    {{ data.start_date }}
                  </td> <td
                    class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-gray-900 sm:pl-0"
                  >
                    {{ data.job_benefits }}
                  </td>
                  <td
                    class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-gray-900 sm:pl-0"
                  >
                    {{ data.show_poster }}
                  </td><td
                    class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-gray-900 sm:pl-0"
                  >
                    {{ data.poster_info }}
                  </td><td
                    class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-gray-900 sm:pl-0"
                  >
                    {{ data.listing_type }}
                  </td><td
                    class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-gray-900 sm:pl-0"
                  >
                    {{ data.last_scrapped_date }}
                  </td><td
                    class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-gray-900 sm:pl-0"
                  >
                    {{ data.is_draft }}
                  </td>
                </tr>
              </tbody>
            </table>
          </div>
        </div>
      </div>
      </div>
      </div>
</template>
<script setup lang="ts">
import { defineEmits, defineProps } from 'vue'

const emit = defineEmits(["openSidebar"]);

const props = defineProps ({
    jobDetails: { type: Object }
})

</script>
