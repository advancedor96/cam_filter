<template>
  <div class="hello">
        <v-slider
          v-model="mark_val"
          :max="10"
          :min="0"
          :step="1"
        ></v-slider>

    <div ref="canvas" width="300" height="300"></div>
hello
  </div>
</template>

<script>
import p5 from "p5";
import "p5/lib/addons/p5.dom";
// p5.dom 方式是學這裡的：https://github.com/ccorcos/circle/blob/master/src/sketch.js

export default {
  name: "HelloWorld",
  data() {
    return {
      ps: null,
      mark_val: 2
    };
  },
  mounted() {
    let script = p => {
      let v = null;
      p.setup = () => {
        // p.createCanvas(window.innerWidth, window.innerHeight).parent(
        //   this.$refs.canvas
        // );
        p.createCanvas(300, 300).parent(this.$refs.canvas);
        var constraints = {
          video: {
            optional: [{ maxFrameRate: 10 }]
          }
        };
        v = p.createCapture(constraints).parent(this.$refs.canvas);
        // v.size(400, 480);
        // v.hide();
        // p.frameRate(30);
      };
      p.draw = () => {
        let iimg = v.get();
        p.tint(0, 153, 204);
        // console.log("iimg", iimg);

        p.image(v, 0, 0, 300, (300 * v.height) / v.width);
        // p.image(v, 0, 0, p.width, (p.width * v.height) / v.width);
        // for (let i = 0; i < p.width; i += this.mark_val) {
        //   for (
        //     let j = 0;
        //     j < (p.width * v.height) / v.width;
        //     j += this.mark_val
        //   ) {
        //     let c = iimg.get(i, j);
        //     p.fill(c);
        //     p.noStroke();
        //     p.rect(i, j, this.mark_val, this.mark_val);
        //   }
        // }
      };
    };
    this.ps = new p5(script);
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
</style>
