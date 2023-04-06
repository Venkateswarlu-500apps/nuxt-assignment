<template>
  <div class="relative">
    <div class="px-4 sm:px-6 lg:px-8">
      <div class="sm:flex sm:items-center">
        <div class="sm:flex-auto"></div>
        <div class="mt-4 sm:ml-16 sm:mt-0 sm:flex-none">
          <button
            type="button"
            class="mt-6 block rounded-md bg-blue-600 px-3 py-2 text-center text-sm font-semibold text-white shadow-sm hover:bg-blue-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
            @click="emit('openSidebar')"
          >
            Add Candidates
          </button>
        </div>
      </div>
      <div class="mt-8 flow-root grid-rows-3 mx-auto my-5 border rounded-lg">
        <div class="-mx-4 -my-2 overflow-x-auto sm:-mx-6 lg:-mx-8">
          <div
            class="inline-block min-w-full py-2 align-middle sm:px-6 lg:px-8"
          >
            <table class="min-w-full divide-y divide-gray-300">
              <thead>
                <tr>
                  <th
                    scope="col"
                    class="py-3.5 pl-4 pr-3 text-center text-sm font-semibold text-gray-900 sm:pl-0"
                  >
                    Name
                  </th>
                  <th
                    scope="col"
                    class="py-3.5 text-left text-sm font-semibold text-gray-900"
                  >
                    Test Type
                  </th>
                  <th
                    scope="col"
                    class="py-3.5 text-left text-sm font-semibold text-gray-900"
                  >
                    Difficulty Level
                  </th>
                  <th
                    scope="col"
                    class="py-3.5 text-left text-sm font-semibold text-gray-900"
                  >
                    Due Date
                  </th>
                  <th
                    scope="col"
                    class="py-3.5 text-left text-sm font-semibold text-gray-900"
                  >
                    Max Time Allowed
                  </th>
                  <th
                    scope="col"
                    class="py-3.5 text-left text-sm font-semibold text-gray-900"
                  >
                    Multiple Attempts Allowed
                  </th>
                  <th
                    scope="col"
                    class="py-3.5 text-left text-sm font-semibold text-gray-900"
                  >
                    Status
                  </th>
                  <th
                    scope="col"
                    class="py-3.5 text-left text-sm font-semibold text-gray-900"
                  >
                    Last Modified Date
                  </th>
                </tr>
              </thead>
              <tbody class="divide-y divide-gray-200">
                <tr
                  v-for="(data, index) in candidatesData.data._rawValue"
                  :key="index"
                >
                  <td
                    class="uppercase whitespace-nowrap py-4 pl-4 pr-3 text-sm text-center font-medium text-gray-900 sm:pl-0"
                  >
                    {{ data.name }}
                  </td>
                  <td
                    class="uppercase whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-gray-900 sm:pl-0"
                  >
                    {{ data.type }}
                  </td>
                  <td
                    class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-gray-900 sm:pl-0"
                  >
                    {{ data.difficulty_level }}
                  </td>
                  <td
                    class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-gray-900 sm:pl-0"
                  >
                    {{ data.due_date }}
                  </td>
                  <td
                    class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-gray-900 sm:pl-0"
                  >
                    {{ data.max_time_allowed }}
                  </td>

                  <td
                    class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-gray-900 sm:pl-0"
                  >
                    {{ data.multiple_attempts_allowed }}
                  </td>
                  <td
                    class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-gray-900 sm:pl-0"
                  >
                    {{ data.status }}
                  </td>
                  <td
                    class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-gray-900 sm:pl-0"
                  >
                    {{ data.last_modified_date }}
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
import { ref, defineProps, defineEmits } from "vue";
const emit = defineEmits(["openSidebar"]);

const props = defineProps({
  candidatesData: { type: Object },
});
const candidatesDetailsFields = ref([{}]);
</script>