<template>
  <div class="container" :style="{'bottom':bottom , 'right':right}">
    <transition name="fade">
      <div @click="scrollToTop" v-if="show" :style="customStyle">
        <slot></slot>
      </div>
    </transition>
  </div>
</template>

<script>
export default {
  props: {
    bottom: {
      type: String,
      default() {
        return '30px';
      },
    },
    right: {
      type: String,
      default() {
        return '30px';
      },
    },
    speed: {
      type: Number,
      default() {
        return 500;
      },
    },
    customStyle: {
      type: Object,
    },
  },
  data() {
    return {
      intervalID: null,
      scrollY: window.scrollY,
      step: 3,
    };
  },
  computed: {
    show() {
      return this.scrollY >= 100;
    },
  },
  methods: {
    scrollToTop() {
      const scrollStep = -this.scrollY / (this.speed / this.step);
      this.intervalID = setInterval(() => {
        if (this.scrollY !== 0) {
          this.setNewScrollPosition(window.scrollY);
          window.scrollBy(0, scrollStep);
        } else {
          this.clearScrollInterval();
        }
      }, this.step);
    },
    clearScrollInterval() {
      if (this.intervalID) {
        clearInterval(this.intervalID);
        this.intervalID = null;
      }
      this.setNewScrollPosition(window.scrollY);
    },
    setNewScrollPosition(position) {
      this.scrollY = position;
    },
  },
  mounted() {
    window.addEventListener('wheel', this.clearScrollInterval);
  },
  destroyed() {
    window.removeEventListener('wheel', this.clearScrollInterval);
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container {
  position: fixed;
}
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.4s;
}
.fade-enter,
.fade-leave-to {
  opacity: 0;
}
</style>
