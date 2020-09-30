<template>
  <div id="app">
    <div class="strap" v-for="(c, i) in colors" :key="i">
      <div :class="c" @click="resetColors"></div>
      <div>
        <div :class="c" :style="{ width: c + '%' }" @click="increaseColor(c)">
          <icon-checkmark v-if="colors[c] === 100" />
          <div v-else>
            <span>{{ colors[c] / 10 }}</span> / 10
          </div>
        </div>
        <div></div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',

  data() {
    return {
      colors: ['green', 'pink', 'orange', 'red'],
      lastCleared: 'green',
      green: 10,
      pink: 20,
      orange: 60,
      red: 100
    }
  },
  computed: {
    style(x) {
      return { width: this[x] + '%' }
    }
  },
  components: {
    IconCheckmark: () => import('@/components/icons/IconCheckmark.vue')
  },
  methods: {
    increaseColor(c) {
      this[c] = Math.min(this[c] + 20, 100)
    },
    resetColors() {
      this.lastCleared = 'green'
      ;(this.green = 10), (this.pink = 20), (this.orange = 60), (this.red = 100)
    }
  }
}
</script>

<style lang="less">
body {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 200vh;
  background: white; // #e9e9e9;
}
.strap {
  display: flex;
  border-radius: 10px;
  width: 100vw;
  height: calc(320px - 120px);
  overflow: hidden;
  margin-bottom: 20px;
  div:first-child {
    background: red;
    width: 25%;
  }
}

.strap {
  div:nth-child(2) {
    display: flex;
    flex-direction: column;
    margin-left: 3px;
    flex: 1;
    > div {
      flex: 1;
      display: flex;
      align-items: center;
      background: white;
      > div:first-child {
        color: white;
        height: 100%;
        transition: 1s width;
      }
      > div:nth-child(2) {
        opacity: 0.3;
        display: flex;
        align-items: center;
        justify-content: center;
        height: 100%;
      }
      p {
        margin: 0 10px;
        white-space: nowrap;
        span {
          font-size: 2rem;
          font-weight: bold;
        }
      }
    }
    > div:not(:last-child) {
      margin-bottom: 3px;
    }
  }
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
</style>
