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
                          >Add Jobs</DialogTitle
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
                    <hr />
                    <div class="relative flex-1 px-4 sm:px-6 py-4">
                      <div v-for="(item, index) in jobs.jobs" :key="index">
                        <div
                          v-if="
                            item.type == 'text' ||
                            item.type == 'number' ||
                            item.type == 'datetime-local' ||
                            item.type == 'url'
                          "
                        >
                          <label
                            class="text-4xl font-black text-gray-900 dark:text-white"
                          />{{ item.label }}
                          <input
                            :placeholder="item.placeholder"
                            :type="item.type"
                            v-model="item.value"
                            :minlength="item.minlength"
                            :maxlength="item.maxlength"
                            :required="item.required"
                            :class="item.class"
                          />
                        </div>
                        <div v-else-if="item.type == 'textarea'">
                          <label
                            class="text-4xl font-black text-gray-900 dark:text-white"
                          />{{ item.label }}
                          <textarea
                            :placeholder="item.placeholder"
                            v-model="item.value"
                            :minlength="item.minlength"
                            :maxlength="item.maxlength"
                            :required="item.required"
                            :class="item.class"
                          />
                        </div>
                        <div v-else-if="item.type == 'select'">
                          <label
                            class="text-4xl font-black text-gray-900 dark:text-white"
                          />{{ item.label }}
                          <select v-model="item.value" :class="item.class">
                            <option
                              v-for="(option, index) in item.options"
                              :key="index"
                              :disabled="option.disabled"
                              :value="option.value"
                            >
                              {{ option.text }}
                            </option>
                          </select>
                        </div>
                      </div>
                    </div>
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
import { defineEmits, ref } from "vue";
import {
  Dialog,
  DialogPanel,
  DialogTitle,
  TransitionChild,
  TransitionRoot,
} from "@headlessui/vue";
import { XMarkIcon } from "@heroicons/vue/24/outline";
import Jobs from "~/data/collection/jobs.json";

const jobs = JSON.parse(JSON.stringify(Jobs));

let jobData = ref({
  title: "",
  industries: "",
  designation: "",
  education_qualification: "",
  skills_description: "",
  external_source: "",
  experience_level: "",
  listed_date: "",
  location_id: 0,
  description: "",
  experience_in_placeof_education: "",
  expiry_date: "",
  apply_url: "",
  operation_type: "",
  work_hours: "",
  working_days: "",
  is_work_remote_allowed: "",
  workplace_type: "",
  employment_status: "",
  company_job_code: "",
  profile_id: 0,
  state: "",
  job_count: "",
  gender: "",
  special_commitments: "string",
  security_clearances: "string",
  languages: "",
  start_date: "",
  job_benefits: "",
  currency_code: "IN",
  salary_incentives: "string",
  salary_high_end: "string",
  salary_low_end: "strin",
  salary_period: "string",
  base_salary: "string",
  show_poster: "",
  poster_info: "",
  listing_type: "",
  last_scrapped_date: "",
  is_draft: "",
});

const open = ref(true);

const emit = defineEmits(["saveJob"]);

const add = () => {
  jobs.jobs.forEach((item: any) => {
    jobData == item.key ? (jobData = item.value) : "";
    console.log("----------jobData>", jobData)
  });
  console.log("jobData---->", jobData);

  let body = jobData;

  // emit("saveJob", body);
  console.log("-------body", body);
  open.value = false;
};
</script>