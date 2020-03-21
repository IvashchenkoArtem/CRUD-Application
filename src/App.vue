<template>
  <div id="app">
    <h1>CRUD Application</h1>
    <hr />
    <!-- <AddString @add-string="addString" />
    <Table v-bind:strings="strings" @remove-string="removeString" />-->
    <router-view />
  </div>
</template>


<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
