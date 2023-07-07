<template>
  <div id="app">
    <Header />
    <Tab/>
    <!-- <WaterFall/> -->
    <!-- <HelloWorld/> -->
    <LocalImg/> 
    <Dialog/> 

  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Tab from "./components/Tab.vue";
// import HelloWorld from './components/HelloWorld.vue'
// import WaterFall from "./components/WaterFall.vue";
import LocalImg from "./components/LocalImg.vue";
import Dialog from "./components/Dialog.vue";


// 随机图片api
// https://source.unsplash.com/random 

export default {
  name: 'App',
  components: {
    Header,
    Tab,
    // HelloWorld,
    // WaterFall,
    LocalImg,
    Dialog
  },

}
</script>

<style>
html {
  ::-webkit-scrollbar {
    display: none;
  }
}
.waterfall-item {
    opacity: 0;
    transform: translateY(200px);
    animation: fade-in-up 3s ease-out both;
  }

  @keyframes fade-in-up {
    from {
      opacity: 0;
      transform: translateY(200px);
    }

    to {
      opacity: 1;
      transform: translateY(0);
    }
  }
  .waterfall-item:nth-child(1) {
  animation-duration: 2s;
}

.waterfall-item:nth-child(2) {
  animation-duration: 2.5s;
}

.waterfall-item:nth-child(3) {
  animation-duration: 3s;
}

.waterfall-item:nth-child(4) {
  animation-duration: 3.5s;
}

.waterfall-item:nth-child(5) {
  animation-duration: 4s;
}

.waterfall-item.loading {
  animation: loading-animation 1s infinite linear;
}



</style>
