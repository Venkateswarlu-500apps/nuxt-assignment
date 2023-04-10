<template>
  <div class="relative">
    <div class="px-4 sm:px-6 lg:px-8">
      <div class="sm:items-center">
        <div class="mt-4 sm:mt-0 sm:flex-none">
          <button
            class="mt-6 px-3 py-2 text-center text-sm shadow-sm block bg-green-500 rounded-md text-white font-medium hover:bg-green-700 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
            type="button"
            @click="emit('openAddContact')"
          >
            Add Contact
          </button>
        </div>
        <div>
          <ul
            role="list"
            class="grid grid-cols-1 gap-6 sm:grid-cols-2 lg:grid-cols-4 mt-8"
          >
            <li
              v-for="(contact, index) in getContacts"
              :key="index"
              class="col-span-1 border-2 divide-y divide-gray-200 rounded-lg bg-white shadow"
            >
              <div
                class="flex w-full items-center justify-between space-x-6 p-6"
              >
                <div class="flex-1 truncate">
                  <div class="flex items-center space-x-3">
                    <h3 class="truncate text-xl font-extrabold text-gray-900">
                      Name -
                    </h3>
                    <span
                      class="truncate inline-block capitalize flex-shrink-0 rounded-md bg-blue-100 px-2 py-0.5 text-xl font-medium text-blue-800"
                      >{{ contact.name }}</span
                    >
                  </div>
                  <div class="flex items-center space-x-3 mt-4">
                    <h3 class="text-xl font-extrabold text-gray-900">
                      Phone -
                    </h3>
                    <span
                      class="truncate inline-block capitalize flex-shrink-0 rounded-md bg-blue-100 px-2 py-0.5 text-xl font-medium text-blue-800"
                      >{{ contact.phone_number }}</span
                    >
                  </div>
                  <div class="flex items-center space-x-3 mt-4">
                    <h3 class="text-xl font-extrabold text-gray-900">
                      Country -
                    </h3>
                    <span
                      class="truncate inline-block capitalize flex-shrink-0 rounded-md bg-blue-100 px-2 py-0.5 text-xl font-medium text-blue-800"
                      >{{ contact.country }}</span
                    >
                  </div>
                  <div class="flex justify-end">
                    <button
                      href="#"
                      class="text-gray-600 hover:text-blue-600 mt-[-14.6rem]"
                      @click="emit('editContactData', contact, index)"
                    >
                      <PencilSquareIcon class="h-6 w-6" aria-hidden="true" />
                    </button>
                    <button
                      href="#"
                      class="text-gray-600 hover:text-red-600 mt-[-14.6rem]"
                      @click="open = true"
                    >
                      <TrashIcon class="h-6 w-6" aria-hidden="true" />
                    </button>
                  </div>
                </div>
              </div>
              <TransitionRoot as="template" :show="open">
                <Dialog as="div" class="relative z-10" @close="open = false">
                  <TransitionChild
                    as="template"
                    enter="ease-out duration-300"
                    enter-from="opacity-0"
                    enter-to="opacity-100"
                    leave="ease-in duration-200"
                    leave-from="opacity-100"
                    leave-to="opacity-0"
                  >
                    <div
                      class="fixed inset-0 bg-gray-500 bg-opacity-75 transition-opacity"
                    />
                  </TransitionChild>

                  <div class="fixed inset-0 z-10 overflow-y-auto">
                    <div
                      class="flex min-h-full items-end justify-center p-4 text-center sm:items-center sm:p-0"
                    >
                      <TransitionChild
                        as="template"
                        enter="ease-out duration-300"
                        enter-from="opacity-0 translate-y-4 sm:translate-y-0 sm:scale-95"
                        enter-to="opacity-100 translate-y-0 sm:scale-100"
                        leave="ease-in duration-200"
                        leave-from="opacity-100 translate-y-0 sm:scale-100"
                        leave-to="opacity-0 translate-y-4 sm:translate-y-0 sm:scale-95"
                      >
                        <DialogPanel
                          class="relative transform overflow-hidden rounded-lg bg-white px-4 pb-4 pt-5 text-left shadow-xl transition-all sm:my-8 sm:w-full sm:max-w-lg sm:p-6"
                        >
                          <div
                            class="bg-white flex flex-col h-full py-3.5 rounded-lg border"
                          >
                            <div class="px-4 sm:px-6">
                              <div class="flex items-start justify-between h-7">
                                <DialogTitle
                                  class="text-base font-semibold leading-6 text-gray-900"
                                  >Delete Contact</DialogTitle
                                >
                                <div class="ml-3 flex h-7 items-center">
                                  <button
                                    type="button"
                                    class="rounded-md mb-3 text-black hover:text-gray-700 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:ring-offset-2"
                                    @click="open = false"
                                  >
                                    <XMarkIcon
                                      class="h-6 w-6"
                                      aria-hidden="true"
                                    />
                                  </button>
                                </div>
                              </div>
                            </div>
                            <div class="h-auto">
                              <div class="mx-auto">
                                <div class="text-center mb-0 rounded-0">
                                  <div class="flex justify-end mt-4">
                                    <button
                                      type="button"
                                      class="border rounded-md bg-gray-600 py-2 px-3 text-sm font-semibold text-white shadow-sm hover:bg-gray-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600 mr-3"
                                      @click="open = false"
                                    >
                                      Cancel
                                    </button>
                                    <button
                                      type="button"
                                      class="rounded-md bg-red-600 py-2 px-4 text-sm font-semibold text-white shadow-sm hover:bg-red-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
                                      @click="emit('deleteContact', index), open = false"
                                    >
                                      Delete
                                    </button>
                                  </div>
                                </div>
                              </div>
                            </div>
                          </div>
                        </DialogPanel>
                      </TransitionChild>
                    </div>
                  </div>
                </Dialog>
              </TransitionRoot>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup lang="ts">
import { defineEmits, defineProps, ref } from "vue";
import {
  FaceSmileIcon,
  PencilSquareIcon,
  TrashIcon,
  XMarkIcon,
} from "@heroicons/vue/24/outline";
import {
  Dialog,
  DialogPanel,
  DialogTitle,
  TransitionChild,
  TransitionRoot,
} from "@headlessui/vue";

const emit = defineEmits([
  "openAddContact",
  "editContactData",
  "deleteContact",
]);
const open = ref(false);
const props = defineProps({
  getContacts: Array,
});
</script>