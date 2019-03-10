<template>
  <div id="app">
    <keep-alive>
      <fake-google v-if="panic" />
      <component v-if="!panic" :is="dynamicComponent"></component>
    </keep-alive>
  </div>
</template>

<script>
import Main from "./components/Main.vue";
import GifBoard from "./components/GifBoard.vue";
import FakeGoogle from "./components/FakeGoogle.vue";

export default {
  name: "app",
  tags:"",
  components: {
    Main,
    GifBoard,
    FakeGoogle
  },
  data() {
    return {
      dynamicComponent: Main,
      panic:false
    };
  },
  methods: {
    showBoard(tags) {
      this.tags = tags;
      this.dynamicComponent = GifBoard
    },
    panicButton(){
      this.panic = !this.panic;
    }
  }
};
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Paytone+One');

body {
  font-family: 'Paytone One', sans-serif;
  width: 100wh;
  height: 100vh;
  color: #fff;
  background: linear-gradient(-45deg, #ee7752, #e73c7e, #23a6d5, #23d5ab);
  background-size: 400% 400%;
  -webkit-animation: Gradient 15s ease infinite;
  -moz-animation: Gradient 15s ease infinite;
  animation: Gradient 15s ease infinite;
}

#app{
  height: 100%;
}


@-webkit-keyframes Gradient {
  0% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}

@-moz-keyframes Gradient {
  0% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}

@keyframes Gradient {
  0% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}
</style>

