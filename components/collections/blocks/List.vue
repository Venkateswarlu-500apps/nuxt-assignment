<template>
  <div class="relative">
    <div class="px-4 sm:px-6 lg:px-8">
      <div class="sm:items-center">
        <div class="mt-4 sm:mt-0 sm:flex-none">
          <button
            class="mt-6 px-3 py-2 text-center text-sm shadow-sm block bg-green-500 rounded-md text-white font-medium hover:bg-green-700 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
            type="button"
            @click="emit('openAddBlocks')"
          >
            Add Blocks
          </button>
        </div>
        <div>
          <h1 class="text-gray-800 font-black text-center text-4xl">
            Blocks Details
          </h1>
          <ul
            role="list"
            class="grid grid-cols-1 gap-6 sm:grid-cols-2 lg:grid-cols-4 mt-8"
          >
            <li
              v-for="(block, index) in getBolcksData"
              :key="index"
              class="col-span-1 border-2 divide-y divide-gray-200 rounded-lg bg-white shadow"
            >
              <div
                class="flex w-full items-center justify-between space-x-6 p-6"
              >
                <div class="flex-1 truncate">
                  <div class="flex items-center space-x-3">
                    <h3 class="truncate text-sm font-medium text-gray-900">
                      Block Name -
                    </h3>
                    <span
                      class="inline-block capitalize flex-shrink-0 rounded-md bg-green-100 px-2 py-0.5 text-xl font-medium text-green-800"
                      >{{ block.name }}</span
                    >
                  </div>
                  <div class="flex items-center space-x-3 mt-4">
                    <h3 class="truncate text-sm font-medium text-gray-900">
                      Block Category -
                    </h3>
                    <span
                      class="inline-block capitalize flex-shrink-0 rounded-md bg-green-100 px-2 py-0.5 text-xl font-medium text-green-800"
                      >{{ block.category }}</span
                    >
                  </div>
                  <div class="flex justify-end">
                    <button
                      href="#"
                      class="text-gray-600 hover:text-blue-600 mt-[-8.1rem]"
                      @click="emit('editBlocks', block)"
                    >
                      <PencilSquareIcon class="h-6 w-6" aria-hidden="true" />
                    </button>
                    <button
                      href="#"
                      class="text-gray-600 hover:text-red-600 mt-[-8.1rem]"
                      @click="emit('deleteBlocks', block, index)"
                    >
                      <TrashIcon class="h-6 w-6" aria-hidden="true" />
                    </button>
                  </div>
                </div>
              </div>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup lang="ts">
import { defineEmits, defineProps } from "vue";
import { PencilSquareIcon, TrashIcon } from "@heroicons/vue/24/outline";

const emit = defineEmits(["openAddBlocks", "editBlocks", "deleteBlocks"]);

const props = defineProps({
  getBolcksData: Array,
});
</script>