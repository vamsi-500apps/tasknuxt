<template>
  <div class="border-b border-gray-200 bg-white px-4 py-5 sm:px-6">
    <h3 class="text-base font-semibold leading-6 text-gray-900">employee</h3>
  
  <div class="px-4 sm:px-6 lg:px-8 p-5">
    <div class="sm:flex sm:items-center">
      <div class="sm:flex-auto">
        <h1 class="text-base font-semibold leading-6 text-gray-900">
          EmployeesData
        </h1>
      </div>
      <div class="mt-4 sm:ml-16 sm:mt-0 sm:flex-none">
        <button
          @click="AddEmploye"
          type="button"
          class="block rounded-md bg-indigo-600 px-3 py-2 text-center text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
        >
          Add Employee
        </button>
      </div>
    </div>
    <div class="mt-8 flow-root">
      <div class="-mx-4 -my-2 overflow-x-auto sm:-mx-6 lg:-mx-8">
        <div class="inline-block min-w-full py-2 align-middle sm:px-6 lg:px-8">
          <table class="min-w-full divide-y divide-gray-300">
            <thead>
              <tr>
                <th
                  scope="col"
                  class="whitespace-nowrap py-3.5 pl-4 pr-3 text-left text-sm font-semibold text-gray-900 sm:pl-0"
                >
                  Employee Name
                </th>
                <th
                  scope="col"
                  class="whitespace-nowrap px-2 py-3.5 text-left text-sm font-semibold text-gray-900"
                >
                  Age
                </th>
                <th
                  scope="col"
                  class="whitespace-nowrap px-2 py-3.5 text-left text-sm font-semibold text-gray-900"
                >
                Gender
                </th>
                
                <th
                  scope="col"
                  class="whitespace-nowrap px-2 py-3.5 text-left text-sm font-semibold text-gray-900"
                >
                  Data Of Joining
                </th>
                <th
                  scope="col"
                  class="whitespace-nowrap px-2 py-3.5 text-left text-sm font-semibold text-gray-900"
                >
                  Designation
                </th>
                 <th
                  scope="col"
                  class="relative whitespace-nowrap py-3.5 pl-3 pr-4 sm:pr-0"
                >
                  Action
                </th>
              </tr>
            </thead>
            <tbody class="divide-y divide-gray-200 bg-white">
              <tr v-for="(employee,index) in EmployeesData" :key="index">
                <td
                  class="whitespace-nowrap py-2 pl-4 pr-3 text-sm text-gray-500 sm:pl-0"
                >
                  {{ employee.name }}
                </td>
                <td
                  class="whitespace-nowrap px-2 py-2 text-sm font-medium text-gray-900"
                >
                  {{ employee.age }}
                </td>
                <td
                  class="whitespace-nowrap px-2 py-2 text-center text-sm text-gray-900"
                > 
                  {{ employee.gender}}
                </td>
                <td class="whitespace-nowrap px-2 py-2 text-sm text-gray-500">
                  {{ employee.dateofjoining }}
                </td>
                <td
                  class="whitespace-nowrap px-2 text-center py-2 text-sm text-gray-500"
                >
                  {{ employee.designation }}
                </td>
                <td class="whitespace-nowrap px-2 text-center py-2 text-sm text-gray-500">
                  <button @click="EditEmployee">edit</button>
                </td>
                <td class="whitespace-nowrap px-2 py-2 text-sm text-gray-500">
                  <button @click="deleteData(index)">delete</button>
                </td>
                
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </div>
</div>
</template>

<script setup lang="ts">
import { defineProps, defineEmits } from "vue";
import { TrashIcon } from "@heroicons/vue/24/outline";

const props = defineProps({
  EmployeesData: {
    type: Array,
  },
});
const emit = defineEmits(["slideout","edit","deletedata"]);

//open sidebar for Add
const AddEmploye = () => {
  emit("slideout");
  
};
const EditEmployee = () => {
  emit("edit");
 
  
};
const deleteData=(index:Number)=>{
  emit("deletedata",index)

}
</script>
