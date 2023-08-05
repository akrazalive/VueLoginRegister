<template>
  <div class="dashboard">
    <ul>
      <li><router-link to="/employee/all">All Employees</router-link></li>
      <li><router-link to="/employee/add">Add New Employee</router-link></li>
    </ul>
    <h1>Welcome to the Dashboard!</h1>
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: 'Dashboard'
};
</script>
