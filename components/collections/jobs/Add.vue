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
                    <div class="px-4 sm:px-6">
                      <div class="flex items-start justify-between">
                        <DialogTitle
                          class="text-base font-semibold leading-6 text-gray-900"
                          >Add Jobs</DialogTitle
                        >
                        <div class="ml-3 flex h-7 items-center">
                          <button
                            type="button"
                            class="rounded-md nb-3 bg-white text-gray-400 hover:text-gray-500 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:ring-offset-2"
                            @click="open = false"
                          >
                            <XMarkIcon class="h-6 w-6" aria-hidden="true" />
                          </button>
                        </div>
                      </div>
                    </div>
                    <hr/>
                    <div class="relative mt-6 flex-1 px-4 sm:px-6">
                      <div v-for="(item, index) in jobs.jobs" :key="index">
                      <div v-if="item.type == 'text' || item.type == 'number' || item.type == 'datetime-local' ">
                      <label
                        class="text-4xl font-black text-gray-900 dark:text-white"
                      />{{ item.label }}
                      <input :placeholder="item.placeholder" :type="item.type"
                        class="bg-white appearance-none border-2 border-gray-500  rounded w-full py-2 px-4 text-gray-700 leading-tight focus:outline-none focus:bg-gray-200 focus:border-blue-500"
                      />
                    </div>
                    <div v-else-if="item.type == 'textarea'">
                      <label
                        class="text-4xl font-black text-gray-900 dark:text-white"
                      />{{ item.label }}
                      <textarea :placeholder="item.placeholder" 
                        class="bg-white appearance-none border-2 border-gray-500  rounded w-full py-2 px-4 text-gray-700 leading-tight focus:outline-none focus:bg-gray-200 focus:border-blue-500"
                      />
                    </div>
                    <div v-else-if="item.type == 'select'">
                      <label
                        class="text-4xl font-black text-gray-900 dark:text-white"
                      />{{ item.label }}
                      <select
                        class="bg-white appearance-none border-2 border-gray-500  rounded w-full py-2 px-4 text-gray-700 leading-tight focus:outline-none focus:bg-gray-200 focus:border-blue-500"
                      ><option v-for="(option, index) in item.options" :key="index" :disabled="option.disabled">{{ option.text }}</option>
                    </select>
                    </div>
                      </div>
                    </div>
                    <hr/>
                        <div class=" bg-gray h-auto">
                          <div class="bg-gray-50 mx-auto">
                            <div class="text-center mb-0 rounded-0">
                            <div class="flex justify-end mr-3 mt-4">
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
import { defineProps, ref } from "vue";
import {
  Dialog,
  DialogPanel,
  DialogTitle,
  TransitionChild,
  TransitionRoot,
} from "@headlessui/vue";
import { XMarkIcon } from "@heroicons/vue/24/outline";
import Jobs from "~/data/collection/jobs.json" 

const jobs = JSON.parse(JSON.stringify(Jobs))
console.log("---------jobs", jobs)
// const jobs = ref({
//   title: "",
//   industries: "",
//   designation: "",
//   educationQualification: "",
//   skillsDescription: "",
//   externalSource: "",
//   experienceLevel: "",
//   listedDate: "",
//   locationId: 0,
//   description: "",
//   experienceInPlaceofEducation: "",
//   expiryDate: "",
//   applyUrl: "",
//   operationType: "",
//   workHours: "",
//   workingDays: "",
//   isWorkRemoteAllowed: 0,
//   workplaceType: "",
//   employmentStatus: "",
//   companyJobCode: "",
//   profileId: 0,
//   state: "",
//   jobCount: 0,
//   gender: "",
//   specialCommitments: "",
//   securityClearances: "",
//   languages: "",
//   startDate: "",
//   jobBenefits: "",
//   currencyCode: "",
//   salaryIncentives: "",
//   salaryHighEnd: "",
//   salaryLowEnd: "",
//   salaryPeriod: "",
//   baseSalary: "",
//   showPoster: "",
//   posterInfo: "",
//   listingType: "",
//   lastScrappedDate: "",
//   isDraft: 0,
//   uid: "3fa85f64-5717-4562-b3fc-2c963f66afa6",
//   id: 0,
//   createdDate: "",
// });

const open = ref(true);

const add = () => {
  let data = {
  // title: jobs.value.title,
  // industries: jobs.value.industries,
  // designation: jobs.value.designation,
  // education_qualification: jobs.value.educationQualification,
  // skills_description: "",
  // external_source: jobs.value.externalSource,
  // experience_level: jobs.value.experienceLevel,
  // listed_date: jobs.value.listedDate,
  // location_id: 0,
  // description: "string",
  // experience_in_placeof_education: "string",
  // expiry_date: "2023-04-07T14:07:36.413Z",
  // apply_url: "string",
  // operation_type: "create",
  // work_hours: "string",
  // working_days: "string",
  // is_work_remote_allowed: 0,
  // workplace_type: "onsite",
  // employment_status: "ft",
  // company_job_code: "string",
  // profile_id: 0,
  // state: closed,
  // job_count: 0,
  // gender: "male",
  // special_commitments: "string",
  // security_clearances: "string",
  // languages: "string",
  // start_date: "2023-04-07T14:07:36.413Z",
  // job_benefits: "string",
  // currency_code: "string",
  // salary_incentives: "string",
  // salary_high_end: "string",
  // salary_low_end: "strin",
  // salary_period: "string",
  // base_salary: "string",
  // show_poster: "yes",
  // poster_info: "name",
  // listing_type: "basic",
  // last_scrapped_date: jobs.value.lastScrappedDate,
  // is_draft: 0
}
}
</script>