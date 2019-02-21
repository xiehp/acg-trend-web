<template>
  <div class="BackgroundStars">
    <canvas style="position: fixed; z-index: 0;" id="Background_Stars"></canvas>
  </div>
</template>

<script>
  export default {
    props: {},
    mounted() {
      console.log("begin Background_Stars");
      let backgroundStars = document.getElementById("Background_Stars");
      let ctx = backgroundStars.getContext("2d");
      backgroundStars.width = window.innerWidth;
      backgroundStars.height = window.innerHeight;
      let w = backgroundStars.width;
      let h = backgroundStars.height;

      let pointCount = 400;
      let points = [];
      // var X, Y;
      // var angle = 0.01;
      let centerX = w * 0.5,
        centerY = h * 0.5;
      /** 旋转最大距离 */
        // var range = centerX < centerY ? centerX - 10 : centerY - 10;
      let range = centerY - 10;
      /** 粒子距离 */
      let spacing = range / pointCount;
      /** 旋转角速度(X度/每秒) */
      let angleSpeed = 0.003;
      /** 粒子大小 */
      let pointSize = 4;

      /** 每秒多少帧 */
      let fps = 15;
      /** 上次执行的时刻 */
      let last = new Date().getTime() / 1000 * 1000;
      console.info(last);

      console.info("range:" + range);
      console.info("spacing:" + spacing);

      let part = function (x, y, ix, iy, vx, vy, angle, dist) {
        this.x = x;
        this.y = y;
        // this.ix = ix;
        // this.iy = iy;
        // this.vx = vx;
        // this.vy = vy;
        this.angle = angle;
        this.dist = dist;
      };

      function init() {
        let x, y, ix, iy, vx, vy, angle, dist;
        for (let i = 0; i < pointCount; i++) {
          // ix = x;
          // iy = y;
          // vx = random(-1, 1);
          // vy = random(-1, 1);
          // rand = random(-80, 100);
          // dist = part_count / 2000 + i/5.0;
          dist = i * spacing;
          angle = 1;

          points.push(new part(x, y, ix, iy, vx, vy, angle, dist));
        }
      }

      init();

      function bg() {
        ctx.fillStyle = '#000000';
        ctx.globalAlpha = 0.5;
        ctx.fillRect(0, 0, backgroundStars.width, backgroundStars.height);
      }

      // function distance(dx,dy){
      //     return Math.sqrt(dx * dx + dy * dy);
      // }

      function draw() {
        for (let i = 0; i < points.length; i++) {
          let point = points[i];

          point.angle += angleSpeed / fps;
          // point.x = centerX + Math.cos(i + point.angle) * (point.dist * i * 0.1);
          // point.y = centerY + Math.sin(i + point.angle) * (point.dist);
          point.x = centerX + Math.cos(i + point.angle) * (point.dist * i * 0.1);
          point.y = centerY + Math.sin(i + point.angle) * (point.dist);
          ctx.fillStyle = '#FFFFFF';
          ctx.fillRect(point.x, point.y, pointSize, pointSize);
        }
      }


      function loop() {
        // 执行时的时间
        let now = new Date().getTime();
        let elapsed = now - last;
        // 经过了足够的时间
        let fpsInterval = 1000 / fps;
        if (elapsed >= fpsInterval) {
          // console.info(new Date());
          last = now - (elapsed % fpsInterval);
          bg();
          draw();
        }

        // requestAnimationFrame(loop);
        setTimeout(loop, fpsInterval - elapsed % fpsInterval);
      }

      loop();

      function resize() {
        backgroundStars.width = window.innerWidth;
        backgroundStars.height = window.innerHeight;
        centerX = window.innerWidth * 0.5;
        centerY = window.innerHeight * 0.5;
      }

      // function random(min, max) {
      //     return Math.random() * (max - min) + min;
      // }

      window.onresize = resize;
    },
  }
</script>
