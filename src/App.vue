<template>
  <div id="app">
    <canvas class="canvas" :width="width" :height="height" ref="stars1"/>
    <router-view/>
    <Footer :mouse-pos="pseudoParallax"/>
  </div>
</template>

<script>
import stars from '@/assets/stars.png';
import Footer from '@/components/Footer.vue';

function Vector(x = 0.0, y = 0.0) {
  this.x = x;
  this.y = y;
  this.length = function () {
    const newX = this.x * this.x;
    const newY = this.y * this.y;
    return Math.sqrt(newX + newY);
  };
  this.multipleByScalar = function (scalar = 1.0) {
    return new Vector(this.x * scalar, this.y * scalar);
  };
  this.devideByScalar = function (scalar = 1.0) {
    if (scalar === 0.0) return Vector();
    return new Vector(this.x / scalar, this.y / scalar);
  };
  this.normalized = function () {
    return this.devideByScalar(this.length());
  };
  this.add = function (otherVector) {
    return new Vector(this.x + otherVector.x, this.y + otherVector.y);
  };
  this.sub = function (otherVector) {
    return new Vector(this.x - otherVector.x, this.y - otherVector.y);
  };
  this.dot = function (otherVector) {
    return (this.x * otherVector.x) + (this.y * otherVector.y);
  };
  this.toString = function () {
    return `Vector[x = ${this.x}, y = ${this.y}]`;
  };
}
export default {
  name: 'Main',
  data: () => ({
    width: 0,
    height: 0,
    toMouseVector: new Vector(1, 1),
    toMouseVectorNormalized: new Vector(1, 1),
    stars,
    cells: null,
    canvas: [],
  }),
  components: {
    Footer,
  },
  methods: {
  },
  mounted() {
    window.addEventListener('resize', () => {
      const { screenX, screenY } = window;
      this.width = screenX;
      this.height = screenY;
    });
    window.addEventListener('mousemove', (e) => {
      const center = new Vector(this.width / 2, this.height / 2);
      const { screenX, screenY } = e;
      const mousePos = new Vector(screenX, screenY);
      this.toMouseVectorNormalized = mousePos.sub(center).normalized();
    });
  },
  destroyed() {
    window.removeEventListener('resize');
  },
  computed: {
    pseudoParallax() {
      return {
        transform: `translate(${this.toMouseVectorNormalized.x * 5}%, ${this.toMouseVectorNormalized.y * 5}%)`,
      };
    },
  },
};
</script>

<style lang="scss">
  * {
    margin: 0;
    padding: 0;
    color: white;
    font-family: 'Roboto', sans-serif;
  }
  #app {
    width: 100vw;
    height: 100vh;
    overflow: hidden;
    background: linear-gradient(#FB8E6A, #471F61);
  }
  #canvas {
    position: fixed;
    top:0;
    left:0;
  }
  .background {
    position: fixed;
    width: 100%;
    height: 100%;
    transform-style: preserve-3d;
  }
</style>
