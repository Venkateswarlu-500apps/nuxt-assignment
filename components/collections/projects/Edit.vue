<template>
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
                    class="flex h-full flex-col overflow-y-scroll bg-white py-3.5 shadow-xl"
                  >
                    <div class="bg-gray-300 px-4 sm:px-6">
                      <div class="flex items-start justify-between h-7">
                        <DialogTitle
                          class="text-base font-semibold leading-6 text-gray-900"
                          >Edit Projects</DialogTitle
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
                              @click="edit()"
                            >
                              Update
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
      </Dialog>
    </TransitionRoot>
  </template>
  
  <script setup lang="ts">
  import { ref, defineProps, onMounted } from 'vue'
  import {
    Dialog,
    DialogPanel,
    DialogTitle,
    TransitionChild,
    TransitionRoot,
  } from '@headlessui/vue'
  const props = defineProps({
    projectsData: Object,
  })
  const open = ref(true)
  const name = ref('')
  const listingTypeName = ref('')
  const details = ref("");
  const specifications = ref("");
  const possessionDate = ref("");
  const ageOfTheProject = ref("");
  const totalProjectArea = ref();
  const visitCount = ref();
  
  const emits = defineEmits(['updateProject'])

  onMounted(() => {
    name.value = props.projectsData.name
    listingTypeName.value = props.projectsData.listing_type_name
    details.value = props.projectsData.details
   specifications.value = props.projectsData.specifications
   possessionDate.value = props.projectsData.possession_date
   ageOfTheProject.value = props.projectsData.age_of_the_project
   totalProjectArea.value = props.projectsData.total_project_area
   visitCount.value = props.projectsData.visit_count
  })
  const edit = () => {
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
      uid: props.projectsData.uid,
    }
    emits('updateProject', body)
    open.value = false
  }
  </script>