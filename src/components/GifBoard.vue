<template>
  <div>
    <div class="gif-content">
      <img v-bind:src="uri">
    </div>
    <div id="fullscreen">
      <img v-on:click="fullScreen" src="@/assets/fullscreen.svg">
    </div>
    <div id="bar"></div>
    <a href="https://github.com/ezesoler/bananita" target="_blank">
      <img class="github-corner" src="@/assets/github.svg" alt="Source!">
    </a>
  </div>
</template>

<style>
body {
  overflow: hidden;
}

.github-corner {
  opacity: 0.4;
  position: fixed;
  left: 0px;
  bottom: 0px;
  width: 24px;
  height: 24px;
  margin: 0.7em;
}

.github-corner:hover {
  opacity: 1;
}

.gif-content {
  margin: 0;
  position: absolute;
  top: 50%;
  left: 50%;
  height: 80%;
  transform: translate(-50%, -50%);
}
.gif-content img {
  height: 100%;
}
#fullscreen {
  position: relative;
}
#fullscreen img {
  padding: 1em;
  position: fixed;
  bottom: 0px;
  right: 0px;
  width: 50px;
  height: 50px;
  cursor: pointer;
  opacity: 0.4;
}

#fullscreen img:hover {
  opacity: 1;
}

.btns img svg path {
  background: rgba(255, 255, 255, 0.4);
  fill: rgba(255, 255, 255, 0.4);
}

.anime {
  animation: loader 60s linear;
  height: 2px;
  width: 0;
  background-color: rgba(255, 255, 255, 0.4);
}

@keyframes loader {
  from {
    width: 0;
  }
  to {
    width: 100%;
  }
}
</style>


<script>
const axios = require("axios");
const defaultGif =
  "https://camo.githubusercontent.com/cd027c3cca58b9fd77945ef5e1e7d5decf986ce4/687474703a2f2f657a65736f6c65722e636f6d2f7269636172646f2f6173736574732f696d672f6c6f6164696e672e676966";
const apiKey = "MCD9MWxaNCntjCzXH67tTBtVNzWUu0dc";
let tagArr = [];
export default {
  data() {
    return {
      uri: defaultGif,
      fs: false
    };
  },
  async mounted() {
    tagArr = this.$root.$children[0].tags.split(",");
    this.getGif();
    this.$nextTick(function() {
      window.setInterval(async () => {
        this.getGif();
      }, 60000);
    });
    window.addEventListener("keypress", e => {
      if (e.code === "Space") {
        this.$root.$children[0].panicButton();
      }
    });
  },
  methods: {
    async getGif() {
      try {
        let tag = tagArr[Math.floor(Math.random() * tagArr.length)];
        const response = await axios.get(
          `http://api.giphy.com/v1/gifs/random?tag=${tag}&api_key=${apiKey}`
        );
        let gif = new Image();
        gif.src = response.data.data.image_original_url;
        gif.onload = () => {
          this.uri = gif.src;
          document.querySelector("#bar").classList.remove("anime");
          document.querySelector("#bar").offsetWidth;
          document.querySelector("#bar").classList.add("anime");
        };
      } catch (error) {
        return defaultGif;
      }
    },
    fullScreen() {
      let elem = document.documentElement;
      if (!this.fs) {
        this.fs = true;
        document.querySelector(
          "#fullscreen img"
        ).src = require("@/assets/restorescreen.svg");

        if (elem.requestFullscreen) elem.requestFullscreen();
        else if (elem.mozRequestFullScreen) elem.mozRequestFullScreen();
        else if (elem.webkitRequestFullscreen) elem.webkitRequestFullscreen();
        else if (elem.msRequestFullscreen) elem.msRequestFullscreen();
      } else {
        this.fs = false;
        document.querySelector(
          "#fullscreen img"
        ).src = require("@/assets/fullscreen.svg");
        if (document.exitFullscreen) document.exitFullscreen();
        else if (document.mozCancelFullScreen) document.mozCancelFullScreen();
        else if (document.webkitExitFullscreen) document.webkitExitFullscreen();
        else if (document.msExitFullscreen) document.msExitFullscreen();
      }
    }
  }
};
</script>

