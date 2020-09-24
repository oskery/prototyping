<template>
  <div id="app">
    <div class="strap strap-1">
      <div class="left">
        <div>
          <div
            class="green"
            :style="{ width: green + '%' }"
            @click="increaseColor('green')"
          >
            <icon-checkmark v-if="green === 100" />
          </div>
          <p v-if="green !== 100"><span>{{ green / 10 }}</span> / 10</p>
        </div>
        <div>
          <div
            class="pink"
            :style="{ width: pink + '%' }"
            @click="increaseColor('pink')"
          >
            <icon-checkmark v-if="pink === 100" />
          </div>
          <p v-if="pink !== 100"><span>{{ pink / 10 }}</span> / 10</p>
        </div>
        <div>
          <div
            class="orange"
            :style="{ width: orange + '%' }"
            @click="increaseColor('orange')"
          >
            <icon-checkmark v-if="orange === 100" />
          </div>
          <p v-if="orange !== 100"><span>{{ orange / 10 }}</span> / 10</p>
        </div>
        <div>
          <div
            class="red"
            :style="{ width: red + '%' }"
            @click="increaseColor('red')"
          >
            <icon-checkmark v-if="red === 100" />
          </div>
          <p v-if="red !== 100"><span>{{ red / 10 }}</span> / 10</p>
        </div>
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
  background: black; // #e9e9e9;
  font-family: 'SquadaOne';
}

.strap {
  display: flex;
  background: white;
  border-radius: 10px;
  width: 562px;
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
    width: 75%;
    margin-right: 3px;
    > div {
      flex: 1;
      display: flex;
      align-items: center;
      > div {
        display: flex;
        align-items:center;
        justify-content: center;
        color: rgba(black, .7);
        height: 100%;
        transition: 1s width;
      }
      p {
        margin: 0 10px;
        white-space: nowrap;        span {
          font-size: 2rem;
          font-weight:bold;
        }
      }
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


@font-face {
  font-family: 'SquadaOne';
  src: url('~@/assets/SquadaOne-Regular.ttf');
  font-weight: normal;
  font-style: normal;
}
</style>
