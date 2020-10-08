<template>
  <div id="app">
    <transition name="fade">
      <router-view/>
    </transition>
  </div>
</template>

<style>
#app {
  height: 100vh;
  width: 100vw;
}

.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-leave-to{
  transition: opacity .1s;
}
.fade-enter, .fade-leave /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
</style>
