<template>
  <div>
    <CollectionsList
      :EmployeesData="employeeDetails"
      @slideout="openSidebar"
      @edit="editData"
      @deletedata="deleteData"
    />
  </div>
  <div v-if="slideout" :key="render">
    <CollectionsAdd @userDetails="submitForm" />
  </div>
  <CollectionsEdit
    v-if="edit"
    :prefillform="prefillData"
    @updateForm="updateFormData"
  />
</template>
<script setup lang="ts">
const slideout = ref(false);
const render = ref(0);
const prefillData = ref({
  name: "",
  age: "",
  gender: "",
  dateOfJoining: "",
  designation: "",
});
const edit = ref(false);
const employeeDetails = ref([]);
onMounted(() => {
    // To get Employee details
  const getEmployes = localStorage.getItem("usersList");
  if(getEmployes&&getEmployes.length)  employeeDetails.value = JSON.parse(getEmployes);
});
const submitForm = (userDetails: any) => {
  employeeDetails.value.push(userDetails);
  console.log("mainDetails--->",typeof employeeDetails.value); 
  localStorage.setItem("usersList", JSON.stringify(userDetails.value));
};
const openSidebar = () => {
  slideout.value = true;
  render.value++;
};
const editData = (employee: any) => {
  prefillData.value = { ...employee };
  edit.value = true;
};
const updateFormData = (employee: any) => {
  employeeDetails.value = employee;
  edit.value = false;
};
const deleteData = (index:any) => {
  employeeDetails.value.splice(index, 1);
  localStorage.setItem("usersList", JSON.stringify(employeeDetails.value));
};
</script>
