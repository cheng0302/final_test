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
    
        var t;
        p5.setup = () => {
          p5.createCanvas(w, h);
          p5.background(255);
          p5.stroke(0, 18);
          p5.noFill();
          t = 0;
        };

        p5.draw = () => {
            var x1 = p5.width * p5.noise(t + 15);
            var x2 = p5.width * p5.noise(t + 25);
            var x3 = p5.width * p5.noise(t + 35);
            var x4 = p5.width * p5.noise(t + 45);
            var y1 = p5.height * p5.noise(t + 55);
            var y2 = p5.height * p5.noise(t + 65);
            var y3 = p5.height * p5.noise(t + 75);
            var y4 = p5.height * p5.noise(t + 85);

            p5.bezier(x1, y1, x2, y2, x3, y3, x4, y4);

            t += 0.005;

            // clear the background every 500 frames using mod (%) operator
            if (p5.frameCount % 750 == 0) {
            p5.background(255);
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