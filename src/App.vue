<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup
import drawflow from './components/drawflow.vue'
</script>

<template>
   <drawflow/>
</template>

<style>
*,
:after,
:before {
  box-sizing: border-box;
  margin: 0;
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
 
}
html {
  padding: 0;
  margin: 0;
  overflow: hidden;
  background: transparent;
}
 body {
  max-width: calc(100vw - 40px);
  max-height:  calc(100vh - 40px);
  margin: 20px;
  padding: 0;
  background: #181818;
  color: #f7f7f7;
}

#app {
  margin: 0px;
  border-radius: 8px; 
  border: 1px solid #494949;
  
}
.el-main {
  padding: 0;
}

</style>
