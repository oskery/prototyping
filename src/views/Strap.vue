<template>
  <div class="strap strap-1">
    <div class="green" @click="resetColors"></div>
    <div>
      <div>
        <div
          class="green"
          :style="{ width: green + '%' }"
          @click="increaseColor('green')"
        >
          <icon-checkmark v-if="green === 100" />
          <div v-else>
            <span>{{ green / 10 }}</span> / 10
          </div>
        </div>
        <div class="green"></div>
      </div>
      <div>
        <div
          class="pink"
          :style="{ width: pink + '%' }"
          @click="increaseColor('pink')"
        >
          <icon-checkmark v-if="pink === 100" />
          <div v-else>
            <span>{{ pink / 10 }}</span> / 10
          </div>
        </div>
        <div class="pink">
          <p v-if="pink !== 100"></p>
        </div>
      </div>
      <div>
        <div
          class="orange"
          :style="{ width: orange + '%' }"
          @click="increaseColor('orange')"
        >
          <icon-checkmark v-if="orange === 100" />
          <p v-else>
            <span>{{ orange / 10 }}</span> / 10
          </p>
        </div>
        <div class="orange"></div>
      </div>
      <div>
        <div
          class="red"
          :style="{ width: red + '%' }"
          @click="increaseColor('red')"
        >
          <icon-checkmark v-if="red === 100" />
          <p v-else>
            <span>{{ red / 10 }}</span> / 10
          </p>
        </div>
        <div class="red"></div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
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
.strap {
  display: flex;
  border-radius: 10px;
  width: 100vw;
  height: calc(320px - 120px);
  overflow: hidden;
  margin-bottom: 20px;
}

.strap-1 {
  div:nth-child(2) > div,
  .left {
    cursor: pointer;
  }
  div:nth-child(2) {
    display: flex;
    flex-direction: column;
    width: 75%;
    margin-right: 3px;
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
        opacity: .3;
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
   div:nth-child(1) {
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

.green-opacity {
  background: rgba(#00e761, 0.2);
}

.orange-opacity {
  background: rgba(#e8733b, 0.2);
}

.pink-opacity {
  background: rgba(#de1d71, 0.2);
}

.green-opacity {
  background: rgba(#00e761, 0.2);
}

button {
  padding: 10px 20px;
  font-size: 1.4rem;
  cursor: pointer;
  margin-right: 20px;
}
</style>
