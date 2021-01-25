<template>
  <div class="container">
    <div id="p5Canvas"></div>
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
          p5.background(255);
          p5.stroke(0);
          p5.noFill();
        };

        p5.draw = () => {
            p5.background(255);
            for (let i = 0; i < 200; i += 20) {
              p5.bezier(
                p5.mouseX - i / 2.0,
                40 + i,
                410,
                20,
                440,
                300,
                240 - i / 16.0,
                300 + i / 8.0
              );
            }
          }
        }

    this.p5Canvas = new P5(sketch, 'p5Canvas');
  },
  unmounted () {
    this.p5Canvas = null;
  },
}
</script>

