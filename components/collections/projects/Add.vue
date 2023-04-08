<template>
  <div>
    <TransitionRoot as="template" :show="open">
      <Dialog as="div" class="relative z-10" @close="open = false">
        <div class="fixed inset-0" />

        <div class="fixed inset-0 overflow-hidden">
          <div class="absolute inset-0 overflow-hidden">
            <div
              class="pointer-events-none fixed inset-y-0 right-0 flex max-w-full pl-10 sm:pl-16"
            >
              <TransitionChild
                as="template"
                enter="transform transition ease-in-out duration-500 sm:duration-700"
                enter-from="translate-x-full"
                enter-to="translate-x-0"
                leave="transform transition ease-in-out duration-500 sm:duration-700"
                leave-from="translate-x-0"
                leave-to="translate-x-full"
              >
                <DialogPanel class="pointer-events-auto w-screen max-w-2xl">
                  <div
                    class="flex h-full flex-col overflow-y-scroll bg-white py-3.5 shadow-xl"
                  >
                    <div class="bg-gray-300 px-4 sm:px-6">
                      <div class="flex items-start justify-between h-7">
                        <DialogTitle
                          class="text-base font-semibold leading-6 text-gray-900"
                          >Add Projects</DialogTitle
                        >
                        <div class="ml-3 flex h-7 items-center">
                          <button
                            type="button"
                            class="rounded-md mb-3 text-black hover:text-gray-700 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:ring-offset-2"
                            @click="open = false"
                          >
                            <XMarkIcon class="h-6 w-6" aria-hidden="true" />
                          </button>
                        </div>
                      </div>
                    </div>
                    <div class="relative flex-1 px-4 sm:px-6 py-4">
                    <label
                      class="text-4xl font-black text-gray-900 dark:text-white"
                    />
                      Project Name
                    <input
                      class= "bg-white appearance-none border-2 border-gray-500 rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:bg-gray-200 focus:border-blue-500"
                      type="text"
                      v-model="name"
                      placeholder="Enter Project Name"
                    />
                    <label
                      class="text-4xl font-black text-gray-900 dark:text-white"
                    />
                      Listing Type Name
                    <input
                      class="bg-white appearance-none border-2 border-gray-500 rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:bg-gray-200 focus:border-blue-500"
                      type="text"
                      v-model="listingTypeName"
                      placeholder="Enter Project Name"

                    />
                    <label
                      class="text-4xl font-black text-gray-900 dark:text-white"
                    />
                    Details
                    <input
                      class="bg-white appearance-none border-2 border-gray-500 rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:bg-gray-200 focus:border-blue-500"
                      type="text"
                      v-model="details"
                      placeholder="Enter Details"

                    />
                    <label
                      class="text-4xl font-black text-gray-900 dark:text-white"
                    />
                    Specifications
                    <input
                      class="bg-white appearance-none border-2 border-gray-500 rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:bg-gray-200 focus:border-blue-500"
                      type="text"
                      v-model="specifications"
                      placeholder="Enter Specifications"

                    />
                    <label
                      class="text-4xl font-black text-gray-900 dark:text-white"
                    />
                    Possession Date
                    <input
                      class="bg-white appearance-none border-2 border-gray-500 rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:bg-gray-200 focus:border-blue-500"
                      type="date"
                      v-model="possessionDate"
                    />
                    <label
                      class="text-4xl font-black text-gray-900 dark:text-white"
                   />
                   Age of the Project
                    <input
                      class="bg-white appearance-none border-2 border-gray-500 rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:bg-gray-200 focus:border-blue-500"
                      type="text"
                      v-model="ageOfTheProject"
                      placeholder="Enter Age of the Project"

                    />
                    <label
                      class="text-4xl font-black text-gray-900 dark:text-white"
                   />
                   Visit Count
                    <input
                      class="bg-white appearance-none border-2 border-gray-500 rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:bg-gray-200 focus:border-blue-500"
                      type="number"
                      v-model="visitCount"
                      placeholder="Enter Visit Count"

                    /> 
                  <hr />
                    <div class="bg-gray-300 h-auto">
                      <div class="mx-auto">
                        <div class="text-center bg-gray-300 mb-0 rounded-0">
                          <div class="flex justify-end mr-3 mt-4 pr-3">
                            <button
                              type="button"
                              class="border rounded-md bg-gray-600 py-2 px-3 text-sm font-semibold text-white shadow-sm hover:bg-gray-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600 mr-3"
                              @click="open = false"
                            >
                              Cancel
                            </button>
                            <button
                              type="button"
                              class="rounded-md bg-blue-600 py-2 px-4 text-sm font-semibold text-white shadow-sm hover:bg-blue-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
                              @click="add()"
                            >
                              Save
                            </button>
                          </div>
                        </div>
                      </div>
                    </div>
                </div>
                </div>
              </DialogPanel>
            </TransitionChild>
          </div>
          </div>
        </div>
      </Dialog>
    </TransitionRoot>
    </div>
  </template>
  
  <script setup lang="ts">
  import { ref } from 'vue'
  import {
    Dialog,
    DialogPanel,
    DialogTitle,
    TransitionChild,
    TransitionRoot,
  } from '@headlessui/vue'
  import { XMarkIcon } from "@heroicons/vue/24/outline";
  const emits = defineEmits(['addProject'])

  const open = ref(true);
  const name = ref("");
  const listingTypeName = ref("");
  const details = ref("");
  const specifications = ref("");
  const possessionDate = ref("");
  const ageOfTheProject = ref("");
  const totalProjectArea = ref();
  const visitCount = ref();

  const add = () => {
    let body = {
      name: name.value,
      listing_type_name: listingTypeName.value,
      category: 'Residential',
      sub_category: 'Apartment',
      status: 'Fully Constructed',
      details: details.value,
      specifications: specifications.value,
      possession_date: possessionDate.value,
      age_of_the_project: ageOfTheProject.value,
      logo_url: "",
      total_project_area: totalProjectArea.value,
      metric: 'sq.ft',
      default_image_url: "",
      visit_count: visitCount.value,
      rera_approved: true,
      approve_status: 'Active',
    }
    emits('addProject', body)
    open.value = false
  }
  </script>