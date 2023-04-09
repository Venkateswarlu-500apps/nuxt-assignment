<template>
    <div class="relative">
      <div class="px-4 sm:px-6 lg:px-8">
        <div class="sm:items-center">
          <div class="mt-4 sm:mt-0 sm:flex-none">
            <button
              class="mt-6 px-3 py-2 text-center text-sm shadow-sm block bg-green-500 rounded-md text-white font-medium hover:bg-green-700 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
              type="button"
              @click="emit('openAddNotes')"
            >
              Add Notes
            </button>
          </div>
          <div>
            <h1 class="text-gray-800 font-black text-center text-4xl">
              Notes Details
            </h1>
            <ul
              role="list"
              class="grid grid-cols-1 gap-6 sm:grid-cols-2 lg:grid-cols-4 mt-8"
            >
              <li
                v-for="(note, index) in getNotesData"
                :key="index"
                class="col-span-1 border-2 divide-y divide-gray-200 rounded-lg bg-white shadow"
              >
                <div
                  class="flex w-full items-center justify-between space-x-6 p-6"
                >
                  <div class="flex-1 truncate">
                    <div class="flex items-center space-x-3">
                      <h3 class="truncate text-xl font-extrabold text-gray-900 ">
                         Entity -
                      </h3>
                      <span
                        class="inline-block capitalize flex-shrink-0 rounded-md bg-blue-100 px-2 py-0.5 text-xl font-medium text-blue-800"
                        >{{ note.entity }}</span
                      >
                    </div>
                    <div class="flex items-center space-x-3 mt-4">
                      <h3 class="text-xl font-extrabold text-gray-900">
                        Notes -
                      </h3>
                      <span
                        class="truncate inline-block capitalize flex-shrink-0 rounded-md bg-blue-100 px-2 py-0.5 text-xl font-medium text-blue-800"
                        >{{ note.note }}</span
                      >
                    </div>
                    <div class="flex justify-end">
                      <button
                        href="#"
                        class="text-gray-600 hover:text-blue-600 mt-[-8.1rem]"
                        @click="emit('editNotes', note)"
                      >
                        <PencilSquareIcon class="h-6 w-6" aria-hidden="true" />
                      </button>
                      <button
                        href="#"
                        class="text-gray-600 hover:text-red-600 mt-[-8.1rem]"
                        @click="emit('deleteNotes', note, index)"
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
  
  const emit = defineEmits(["openAddNotes", "editNotes", "deleteNotes"]);
  
  const props = defineProps({
    getNotesData: Array,
  });
  </script>