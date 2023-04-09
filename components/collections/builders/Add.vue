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
                          >Add Builder</DialogTitle
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
                    <form>
                    <div class="relative flex-1 px-4 sm:px-6 py-4">
                      <label
                        class="text-4xl font-black text-gray-900 dark:text-white"
                      />
                      Builder Name
                      <input
                        class="bg-white appearance-none border-2 border-gray-500 rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:bg-gray-200 focus:border-blue-500"
                        type="text"
                        v-model="builder.name"
                        placeholder="Enter Builder Name"
                      />
                      <label
                        class="text-4xl font-black text-gray-900 dark:text-white"
                      />
                      Email
                      <input
                        class="bg-white appearance-none border-2 border-gray-500 rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:bg-gray-200 focus:border-blue-500"
                        type="email"
                        v-model="builder.email"
                        placeholder="Enter Email"
                      />
                      <label
                        class="text-4xl font-black text-gray-900 dark:text-white"
                      />
                      Phone Number
                      <input
                        class="bg-white appearance-none border-2 border-gray-500 rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:bg-gray-200 focus:border-blue-500"
                        type="number"
                        v-model="builder.phone_number"
                        placeholder="Enter Phone Number"
                      />
                      <label
                        class="text-4xl font-black text-gray-900 dark:text-white"
                      />
                      Established Year
                      <input
                        class="bg-white appearance-none border-2 border-gray-500 rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:bg-gray-200 focus:border-blue-500"
                        type="month"
                        v-model="builder.established_year"
                      />
                      <label
                        class="text-4xl font-black text-gray-900 dark:text-white"
                      />
                      Tag Line
                      <input
                        class="bg-white appearance-none border-2 border-gray-500 rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:bg-gray-200 focus:border-blue-500"
                        type="text"
                        placeholder="Enter Tag Line"
                        v-model="builder.tag_line"
                      />
                      <label
                        class="text-4xl font-black text-gray-900 dark:text-white"
                      />
                      Registration Details
                      <input
                        class="bg-white appearance-none border-2 border-gray-500 rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:bg-gray-200 focus:border-blue-500"
                        type="text"
                        v-model="builder.reg_details"
                        placeholder="Enter Registration Details"
                      />
                      <label
                        class="text-4xl font-black text-gray-900 dark:text-white"
                      />
                      Registration Url
                      <input
                        class="bg-white appearance-none border-2 border-gray-500 rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:bg-gray-200 focus:border-blue-500"
                        type="url"
                        v-model="builder.reg_rera_url"
                        placeholder="Enter Registration Url "
                      />
                      </div>
                      </form>
                      <hr />
                      <div class="h-auto">
                        <div class="mx-auto">
                          <div class="text-center mb-0 rounded-0">
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
import { ref, defineEmits } from "vue";
import {
  Dialog,
  DialogPanel,
  DialogTitle,
  TransitionChild,
  TransitionRoot,
} from "@headlessui/vue";
import { XMarkIcon } from "@heroicons/vue/24/outline";
const emits = defineEmits(["addBuilder"]);

const open = ref(true);
const builder = ref({
  name: "",
  email: "",
  phone_number: "",
  established_year: "",
  logo: "string",
  tag_line: "",
  reg_details: "",
  reg_rera_url: "",
  is_active: true,
});

const add = () => {
  emits("addBuilder", builder);
  open.value = false;
};
</script>