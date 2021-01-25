<template>
  <div class="container">
    <div class="p5Canvas"></div>
  </div>
</template>

<script>
import P5 from 'p5';

export default {
  data() {
    return {
      p5Canvas: null,
    }
  },
  created() {
    const sketch = p5 => {
        let w = 2000;
        let h = 500;

        // let w = window.innerWidth;
        // let h = window.innerHeight;

        p5.setup = () => {
            p5.createCanvas(w, h);
            p5.background(255, 255, 255);
            p5.stroke(0, 0, 0, 20);
        };

        p5.draw = () => {
            p5.randomChord();
            p5.randomChord();

        };

        // create methods:
        p5.randomChord = () => {
          let angle1 = p5.random(0, 2 * p5.PI);
          let xpos1 = 200 + 300 * p5.cos(angle1);
          let ypos1 = 200 + 300 * p5.sin(angle1);

          let angle2 = p5.random(0, 2 * p5.PI);
          let xpos2 = 200 + 300 * p5.cos(angle2);
          let ypos2 = 200 + 300 * p5.sin(angle2);
          
          p5.line(xpos1, ypos1, xpos2, ypos2);
        }
    }

    this.p5Canvas = new P5(sketch, 'p5Canvas');
  },
  unmounted () {
    this.p5Canvas = null;
  },
}
</script>

<style style lang="sass">
  .p5Canvas

    position: absolute
    z-index: 9999
    top: 20
    left: 750

</style>