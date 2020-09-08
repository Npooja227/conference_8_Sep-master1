<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
html,body {
  height: 100%;
}

#app {
  color: #fff;
  overflow-y: scroll;
  overflow-y: auto;
  height: 100%;
}

.pointer {
  cursor: pointer;
}
</style>
