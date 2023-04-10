<template>
  <div>
  <CollectionsList  :EmployeesData="employeeDetails "
    
    @slideout="openSidebar"
  /></div>
  <div v-if="slideout" :key="render">
    <CollectionsAdd @userDetails="submitForm" />
  </div>
</template>
<script setup lang="ts">
const slideout = ref(false);
const render = ref(0);
const employeeDetails=ref([])
const submitForm = (userDetails:any) => {
  console.log("employeeDetails-->",userDetails);
  
  employeeDetails.value.unshift(userDetails);
  localStorage.setItem("usersList", JSON.stringify(userDetails));
};
const openSidebar=()=>{
  
  slideout.value=true;
  render.value++;
}
</script>
