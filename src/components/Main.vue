<template>
  <div class="container">
    <div class="row">
      <div class="center-box p-3">
        <img src="@/assets/bananita.gif" height="200">
        <h1 class="display-4">BANANITA</h1>
        <h6>A random gif every minute!</h6>
        <hr class="my-3">
          <div class="form-row align-items-center">
            <div class="col-auto mx-auto">
              <label class="sr-only" for="inlineFormInputGroup">TAGS</label>
              <div class="input-group mb-2">
                <div class="input-group-prepend">
                  <div class="input-group-text">TAGS:</div>
                </div>
                <input
                  type="search"
                  class="form-control"
                  id="inlineFormInputGroup"
                  placeholder="Tags"
                  v-model="tags"
                  v-on:keyup.enter="showBoard"
                >
              </div>
            </div>
          </div>
        <hr class="my-3">
        <button type="button" class="btn btn-success btn-lg" v-on:click="showBoard">DALE GAS!</button>
      </div>
    </div>
  </div>
</template>

<style>
.center-box {
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 99;
  margin: auto;
  height: 490px;
  width: 400px;
  text-align: center;
  background-color: rgba(255, 255, 255, 0.6);
}

h1 {
  font-family: "Paytone One", sans-serif;
  animation: colorchange 20s infinite alternate;
}

@-webkit-keyframes colorchange {
  0% {
    color: blue;
  }

  10% {
    color: #8e44ad;
  }

  20% {
    color: #1abc9c;
  }

  30% {
    color: #d35400;
  }

  40% {
    color: blue;
  }

  50% {
    color: #34495e;
  }

  60% {
    color: blue;
  }

  70% {
    color: #2980b9;
  }
  80% {
    color: #f1c40f;
  }

  90% {
    color: #2980b9;
  }

  100% {
    color: pink;
  }
}
</style>

<script>
export default {
  data() {
    return {
      tags:"meme,funny,dancing"
    }
  },
  methods: {
    showBoard() {
      if(this.tags == ""){
        this.tags = "meme,funny,dancing";
      }
      this.$root.$children[0].showBoard(this.tags);
    }
  }
};
</script>


