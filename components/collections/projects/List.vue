<template>
  <div class="relative">
    <div class="px-4 sm:px-6 lg:px-8">
      <div class="sm:flex sm:items-center">
        <div class="sm:flex-auto"></div>
        <div class="mt-4 sm:ml-16 sm:mt-0 sm:flex-none">
          <button
            class="mt-6 px-3 py-2 text-center text-sm shadow-sm block bg-green-500 rounded-md text-white font-medium hover:bg-green-700 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
            type="button"
            @click="$emit('openSidebar')"
          >
            Add Projects
          </button>
        </div>
      </div>
      <div>
        <h1 class="text-gray-800 font-black text-center text-4xl">
          Projects Details
        </h1>

        <div class="mt-8 flow-root grid-rows-3 mx-auto my-5 border rounded-lg">
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
                      Project Name
                    </th>
                    <th
                      scope="col"
                      class="py-3.5 pl-4 pr-3 text-center text-sm font-semibold text-gray-900 sm:pl-0"
                    >
                      Listing Type Name
                    </th>
                    <th
                      scope="col"
                      class="py-3.5 pl-4 pr-3 text-center text-sm font-semibold text-gray-900 sm:pl-0"
                    >
                      Category
                    </th>
                    <th
                      scope="col"
                      class="py-3.5 pl-4 pr-3 text-center text-sm font-semibold text-gray-900 sm:pl-0"
                    >
                      Sub Category
                    </th>
                    <th
                      scope="col"
                      class="py-3.5 pl-4 pr-3 text-center text-sm font-semibold text-gray-900 sm:pl-0"
                    >
                      Status
                    </th>
                    <th
                      scope="col"
                      class="py-3.5 pl-4 pr-3 text-center text-sm font-semibold text-gray-900 sm:pl-0"
                    >
                      Details
                    </th>
                    <th
                      scope="col"
                      class="py-3.5 pl-4 pr-3 text-center text-sm font-semibold text-gray-900 sm:pl-0"
                    >
                      Specifications
                    </th>
                    <th
                      scope="col"
                      class="py-3.5 pl-4 pr-3 text-center text-sm font-semibold text-gray-900 sm:pl-0"
                    >
                      Possession Date
                    </th>
                    <th
                      scope="col"
                      class="py-3.5 pl-4 pr-3 text-center text-sm font-semibold text-gray-900 sm:pl-0"
                    >
                      Age of the Project
                    </th>
                    <th
                      scope="col"
                      class="py-3.5 pl-4 pr-3 text-center text-sm font-semibold text-gray-900 sm:pl-0"
                    >
                      Visit Count
                    </th>
                    <th
                      scope="col"
                      class="py-3.5 pl-4 pr-3 text-center text-sm font-semibold text-gray-900 sm:pl-0"
                    ></th>
                  </tr>
                </thead>
                <tbody class="divide-y divide-gray-200">
                  <tr v-for="(project, index) in projectData" :key="index">
                    <td
                      class="uppercase whitespace-nowrap py-4 pl-4 pr-3 text-sm text-center font-medium text-gray-900 sm:pl-0"
                    >
                      {{ project.name ? project.name : '- - -' }}
                    </td>
                    <td
                      class="uppercase whitespace-nowrap py-4 pl-4 pr-3 text-sm text-center font-medium text-gray-900 sm:pl-0"
                    >
                      {{ project.listing_type_name ? project.listing_type_name : '- - -' }}
                    </td>
                    <td
                      class="uppercase whitespace-nowrap py-4 pl-4 pr-3 text-sm text-center font-medium text-gray-900 sm:pl-0"
                    >
                      {{ project.category ? project.category : '- - -'}}
                    </td>
                    <td
                      class="uppercase whitespace-nowrap py-4 pl-4 pr-3 text-sm text-center font-medium text-gray-900 sm:pl-0"
                    >
                      {{ project.sub_category ? project.sub_category : '- - -' }}
                    </td>
                    <td
                      class="uppercase whitespace-nowrap py-4 pl-4 pr-3 text-sm text-center font-medium text-gray-900 sm:pl-0"
                    >
                      {{ project.status ? project.status : '- - -' }}
                    </td>
                    <td
                      class="uppercase whitespace-nowrap py-4 pl-4 pr-3 text-sm text-center font-medium text-gray-900 sm:pl-0"
                    >
                      {{ project.details ? project.details : '- - -' }}
                    </td>
                    <td
                      class="uppercase whitespace-nowrap py-4 pl-4 pr-3 text-sm text-center font-medium text-gray-900 sm:pl-0"
                    >
                      {{ project.specifications ? project.specifications : '- - -' }}
                    </td>
                    <td
                      class="uppercase whitespace-nowrap py-4 pl-4 pr-3 text-sm text-center font-medium text-gray-900 sm:pl-0"
                    >
                      {{ project.possession_date ? project.possession_date : '- - -' }}
                    </td>
                    <td
                      class="uppercase whitespace-nowrap py-4 pl-4 pr-3 text-sm text-center font-medium text-gray-900 sm:pl-0"
                    >
                      {{ project.age_of_the_project ? project.age_of_the_project: '- - -' }}
                    </td>
                    <td
                      class="uppercase whitespace-nowrap py-4 pl-4 pr-3 text-sm text-center font-medium text-gray-900 sm:pl-0"
                    >
                      {{ project.visit_count ? project.visit_count : '- - -' }}
                    </td>
                    <td
                      class="relative whitespace-nowrap py-4 pl-3 pr-4 text-right text-sm font-medium sm:pr-0"
                    >
                      <button
                        href="#"
                        class="text-gray-600 hover:text-blue-600 mr-4"
                        @click="emits('editProject', project, index)"
                      >
                        <PencilSquareIcon class="h-6 w-6" aria-hidden="true" />
                      </button>
                      <button
                        href="#"
                        class="text-gray-600 hover:text-red-600 mr-4"
                        @click="emits('deleteProject', project, index)"
                      >
                        <TrashIcon class="h-6 w-6" aria-hidden="true" />
                      </button>
                    </td>
                  </tr>
                </tbody>
              </table>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
  
  <script setup lang="ts">
import { ref, defineProps, defineEmits } from "vue";
import { PencilSquareIcon, TrashIcon } from "@heroicons/vue/24/outline";

const props = defineProps({
  projectData: { type: Object },
});
const emits = defineEmits(["openSidebar", "editProject", "deleteProject"]);
</script>