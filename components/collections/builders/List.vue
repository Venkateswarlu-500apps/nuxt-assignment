<template>
  <div class="relative">
    <div class="px-4 sm:px-6 lg:px-8">
      <div class="sm:flex sm:items-center">
        <div class="sm:flex-auto"></div>
        <div class="mt-4 sm:ml-16 sm:mt-0 sm:flex-none">
          <button
            class="mt-6 px-3 py-2 text-center text-sm shadow-sm block bg-green-500 rounded-md text-white font-medium hover:bg-green-700 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
            type="button"
            @click="$emit('openAddSidebar')"
          >
            Add Builders
          </button>
        </div>
      </div>
      <div>
        <h1 class="text-gray-800 font-black text-center text-4xl">
          Builder Details
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
                      Builder Name
                    </th>
                    <th
                      scope="col"
                      class="py-3.5 pl-4 pr-3 text-center text-sm font-semibold text-gray-900 sm:pl-0"
                    >
                      Email
                    </th>
                    <th
                      scope="col"
                      class="py-3.5 pl-4 pr-3 text-center text-sm font-semibold text-gray-900 sm:pl-0"
                    >
                      Phone Number
                    </th>
                    <th
                      scope="col"
                      class="py-3.5 pl-4 pr-3 text-center text-sm font-semibold text-gray-900 sm:pl-0"
                    >
                      Established Year
                    </th>
                    <th
                      scope="col"
                      class="py-3.5 pl-4 pr-3 text-center text-sm font-semibold text-gray-900 sm:pl-0"
                    >
                      Tag Line
                    </th>
                    <th
                      scope="col"
                      class="py-3.5 pl-4 pr-3 text-center text-sm font-semibold text-gray-900 sm:pl-0"
                    >
                      Registration Details
                    </th>
                    <th
                      scope="col"
                      class="py-3.5 pl-4 pr-3 text-center text-sm font-semibold text-gray-900 sm:pl-0"
                    >
                      Registration Url
                    </th>
                    <th
                      scope="col"
                      class="py-3.5 pl-4 pr-3 text-center text-sm font-semibold text-gray-900 sm:pl-0"
                    >
                      Active
                    </th>
                    <th
                      scope="col"
                      class="py-3.5 pl-4 pr-3 text-center text-sm font-semibold text-gray-900 sm:pl-0"
                    ></th>
                  </tr>
                </thead>
                <tbody class="divide-y divide-gray-200">
                  <tr v-for="(builder, index) in builderData" :key="index">
                    <td
                      class="capitalize whitespace-nowrap py-4 pl-4 pr-3 text-sm text-center font-medium text-gray-900 sm:pl-0"
                    >
                      {{ builder.name }}
                    </td>
                    <td
                      class="whitespace-nowrap py-4 pl-4 pr-3 text-sm text-center font-medium text-gray-900 sm:pl-0"
                    >
                      {{ builder.email }}
                    </td>
                    <td
                      class="capitalize whitespace-nowrap py-4 pl-4 pr-3 text-sm text-center font-medium text-gray-900 sm:pl-0"
                    >
                      {{ builder.phone_number }}
                    </td>
                    <td
                      class="capitalize whitespace-nowrap py-4 pl-4 pr-3 text-sm text-center font-medium text-gray-900 sm:pl-0"
                    >
                      {{ builder.established_year }}
                    </td>
                    <td
                      class="capitalize whitespace-nowrap py-4 pl-4 pr-3 text-sm text-center font-medium text-gray-900 sm:pl-0"
                    >
                      {{ builder.tag_line }}
                    </td>
                    <td
                      class="capitalize whitespace-nowrap py-4 pl-4 pr-3 text-sm text-center font-medium text-gray-900 sm:pl-0"
                    >
                      {{ builder.reg_details }}
                    </td>
                    <td
                      class="underline whitespace-nowrap py-4 pl-4 pr-3 text-sm text-center font-medium text-blue-500 sm:pl-0"
                    >
                    <a :href="builder.reg_rera_url" target="_blank"> {{ builder.reg_rera_url }} </a>
                    </td>
                    <td
                      class="capitalize whitespace-nowrap py-4 pl-4 pr-3 text-sm text-center font-medium text-gray-900 sm:pl-0"
                    >
                      {{ builder.is_active }}
                    </td>
                    <td
                      class="relative whitespace-nowrap py-4 pl-3 pr-4 text-right text-sm font-medium sm:pr-0"
                    >
                      <button
                        href="#"
                        class="text-gray-600 hover:text-blue-600 mr-4"
                        @click="emits('editBuilder', builder)"
                      >
                        <PencilSquareIcon class="h-6 w-6" aria-hidden="true" />
                      </button>
                      <button
                        href="#"
                        class="text-gray-600 hover:text-red-600 mr-4"
                        @click="emits('deleteBuilder', builder, index)"
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
  builderData: Array,
});

const emits = defineEmits(["openAddSidebar", "editBuilder", "deleteBuilder"]);
</script>