<template>
  <div class="home">
    <vue-p5
      @sketch="sketch"
      @preload="preload"
      @setup="setup"
      @draw="draw"
      @keypressed="keyPressed"
      @mousemoved="mouseMoved"
      @mousedragged="mouseDragged"
    ></vue-p5>
  </div>
</template>

<script>
// examples used are
// https://github.com/Kinrany/vue-p5-example and
// http://p5js.org/examples/form-points-and-lines.html

import VueP5 from "vue-p5";
export default {
  name: "home",
  components: {
    "vue-p5": VueP5
  },
  data: () => ({
    red: 255,
    green: 0,
    blue: 0,
    lines: [],
    backgroundImage: null
  }),
  methods: {
    sketch(sketch) {
      sketch.draw = () => {};
    },
    preload(sketch) {
      this.backgroundImage = sketch.loadImage("p5js.png");
    },
    setup(sketch) {
      sketch.createCanvas(400, 400);
      let columns = 8;
      let rows = 15;
      for (let index = 0; index < rows; index++) {
        sketch.translate(15, 15);
        for (let _2index = 0; _2index < columns; _2index++) {
          sketch.translate(15, 15);
          var d = 15;
          var p1 = d;
          var p2 = p1 + d;
          var p3 = p2 + d;
          var p4 = p3 + d;

          sketch.line(p3, p3, p2, p3);
          sketch.line(p2, p3, p2, p2);
          sketch.line(p2, p2, p3, p2);
          sketch.line(p3, p2, p3, p3);
        }
      }
    },
    draw(sketch) {
      const { width, height } = sketch;
    }
  }
};
</script>
