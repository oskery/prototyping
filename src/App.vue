<template>
  <div id="app">
    <div class="strap strap-1">
      <div class="left">
        <div
          class="green"
          :style="{ width: green + '%' }"
          @click="increaseColor('green')"
        ></div>
        <div
          class="pink"
          :style="{ width: pink + '%' }"
          @click="increaseColor('pink')"
        ></div>
        <div
          class="orange"
          :style="{ width: orange + '%' }"
          @click="increaseColor('orange')"
        ></div>
        <div
          class="red"
          :style="{ width: red + '%' }"
          @click="increaseColor('red')"
        ></div>
      </div>
      <div class="right green" @click="resetColors"></div>
    </div>
    <div class="strap strap-2" v-if="false">
      <div class="left">
        <div
          class="green"
          :style="{ width: green + '%' }"
          @click="increaseColor('green')"
        ></div>
        <div
          class="pink"
          :style="{ width: pink + '%' }"
          @click="increaseColor('pink')"
        ></div>
        <div
          class="orange"
          :style="{ width: orange + '%' }"
          @click="increaseColor('orange')"
        ></div>
        <div
          class="red"
          :style="{ width: red + '%' }"
          @click="increaseColor('red')"
        ></div>
      </div>
      <div class="right green" @click="resetColors"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      lastCleared: 'green',
      green: 10,
      pink: 25,
      orange: 60,
      red: 100
    }
  },
  methods: {
    increaseColor(c) {
      this[c] = this[c] + 20
    },
    resetColors() {
      this.lastCleared = 'green'
      ;(this.green = 10), (this.pink = 25), (this.orange = 60), (this.red = 100)
    }
  }
}
</script>

<style lang="less">
body {
  margin: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
  background: #e9e9e9;
}

.strap {
  display: flex;
  background: white;
  border-radius: 10px;
  width: 568px;
  height: calc(320px - 120px);
  overflow: hidden;
  border: 3px solid white;
  margin-bottom: 20px;
}

.strap-1 {
  .left > div,
  .right {
    cursor: pointer;
  }
  .left > div:hover,
  .right:hover {
    filter: brightness(1.2);
  }
  .left {
    display: flex;
    flex-direction: column;
    width: 70%;
    margin-right: 3px;
    > div {
      flex: 1;
      transition: 1s width;
    }
    > div:not(:last-child) {
      margin-bottom: 3px;
    }
  }
  .right {
    flex: 1;
  }
}

.strap-2 {
}

.red {
  background: #e0424d;
}
.orange {
  background: #e8733b;
}
.pink {
  background: #de1d71;
}
.green {
  background: #00e761;
}
button {
  padding: 10px 20px;
  font-size: 1.4rem;
  cursor: pointer;
  margin-right: 20px;
}
</style>
