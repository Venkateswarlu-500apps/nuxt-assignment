<template>
  <TransitionRoot as="template" :show="open">
    <Dialog as="div" class="relative z-10" @close="open = false">
      <TransitionChild as="template" enter="ease-out duration-300" enter-from="opacity-0" enter-to="opacity-100"
        leave="ease-in duration-200" leave-from="opacity-100" leave-to="opacity-0">
        <div class="fixed inset-0 bg-gray-500 bg-opacity-75 transition-opacity" />
      </TransitionChild>

      <div class="fixed inset-0 z-10 overflow-y-auto">
        <div class="flex min-h-full items-end justify-center p-4 text-center sm:items-center sm:p-0">
          <TransitionChild as="template" enter="ease-out duration-300"
            enter-from="opacity-0 translate-y-4 sm:translate-y-0 sm:scale-95"
            enter-to="opacity-100 translate-y-0 sm:scale-100" leave="ease-in duration-200"
            leave-from="opacity-100 translate-y-0 sm:scale-100"
            leave-to="opacity-0 translate-y-4 sm:translate-y-0 sm:scale-95">
            <DialogPanel
              class="relative transform overflow-hidden rounded-lg bg-white px-4 pb-4 pt-5 text-left shadow-xl transition-all sm:my-8 sm:w-full sm:max-w-lg sm:p-6">
              <div class="flex h-full flex-col bg-white py-3.5 border rounded-lg">
                <div class="px-4 sm:px-6">
                  <div class="flex items-start justify-between h-7">
                    <DialogTitle class="text-base font-semibold leading-6 text-gray-900">Edit Project</DialogTitle>
                    <div class="ml-3 flex h-7 items-center">
                      <button type="button"
                        class="rounded-md mb-3 text-black hover:text-gray-700 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:ring-offset-2"
                        @click="open = false">
                        <XMarkIcon class="h-6 w-6" aria-hidden="true" />
                      </button>
                    </div>
                  </div>
                </div>
                <hr />
                <div class="relative flex-1 px-4 sm:px-6 py-4">
                  <label class="text-4xl font-black text-gray-900 dark:text-white" />
                  Project Name
                  <input
                    class="bg-white appearance-none border-2 border-gray-500 rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:bg-gray-200 focus:border-blue-500"
                    type="text" v-model="editData.name" placeholder="Enter Project Name" />
                  <label class="text-4xl font-black text-gray-900 dark:text-white" />
                  Listing Type Name
                  <input
                    class="bg-white appearance-none border-2 border-gray-500 rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:bg-gray-200 focus:border-blue-500"
                    type="text" v-model="editData.listing_type_name" placeholder="Enter Project Name" />
                  <label class="text-4xl font-black text-gray-900 dark:text-white" />
                  Details
                  <input
                    class="bg-white appearance-none border-2 border-gray-500 rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:bg-gray-200 focus:border-blue-500"
                    type="text" v-model="editData.details" placeholder="Enter Details" />
                  <label class="text-4xl font-black text-gray-900 dark:text-white" />
                  Specifications
                  <input
                    class="bg-white appearance-none border-2 border-gray-500 rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:bg-gray-200 focus:border-blue-500"
                    type="text" v-model="editData.specifications" placeholder="Enter Specifications" />
                  <label class="text-4xl font-black text-gray-900 dark:text-white" />
                  Possession Date
                  <input
                    class="bg-white appearance-none border-2 border-gray-500 rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:bg-gray-200 focus:border-blue-500"
                    type="date" v-model="editData.possession_date" />
                  <label class="text-4xl font-black text-gray-900 dark:text-white" />
                  Age of the Project
                  <input
                    class="bg-white appearance-none border-2 border-gray-500 rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:bg-gray-200 focus:border-blue-500"
                    type="text" v-model="editData.age_of_the_project" placeholder="Enter Age of the Project" />
                  <label class="text-4xl font-black text-gray-900 dark:text-white" />
                  Total Project Area
                  <input
                    class="bg-white appearance-none border-2 border-gray-500 rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:bg-gray-200 focus:border-blue-500"
                    type="number" v-model="editData.total_project_area" placeholder="Enter Total Project Area" />
                  <label class="text-4xl font-black text-gray-900 dark:text-white" />
                  Visit Count
                  <input
                    class="bg-white appearance-none border-2 border-gray-500 rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:bg-gray-200 focus:border-blue-500"
                    type="number" v-model="editData.visit_count" placeholder="Enter Visit Count" />
                  <div class="h-auto">
                    <div class="mx-auto">
                      <div class="text-center mb-0 rounded-0">
                        <div class="flex justify-end mt-4">
                          <button type="button"
                            class="border rounded-md bg-gray-600 py-2 px-3 text-sm font-semibold text-white shadow-sm hover:bg-gray-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600 mr-3"
                            @click="open = false">
                            Cancel
                          </button>
                          <button type="button"
                            class="rounded-md bg-blue-600 py-2 px-4 text-sm font-semibold text-white shadow-sm hover:bg-blue-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
                            @click="edit()">
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
import { ref, defineProps, defineEmits } from 'vue'
import {
  Dialog,
  DialogPanel,
  DialogTitle,
  TransitionChild,
  TransitionRoot,
} from '@headlessui/vue'
import { XMarkIcon } from "@heroicons/vue/24/outline";

const props = defineProps({
  editData: Object,
})

const open = ref(true);

const emits = defineEmits(['updateProject'])

const edit = () => {
  emits('updateProject', props.editData)
  open.value = false
}
</script>