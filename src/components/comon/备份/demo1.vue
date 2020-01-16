<template>
  <div id="coolClockWrap">
    <canvas ref="coolClockCanvas" :width="canvas.width" :height="canvas.height"></canvas>
  </div>
</template>

<script>
export default {
  name: "",
  data() {
    return {
      canvas: {
        width: 430,
        height: 430
      },
      L: 0 //基础半径
    };
  },
  mounted() {
    this.drawCoolClock();
  },
  destroyed() {},
  methods: {
    drawCoolClock() {
      let canvas =this.$refs.coolClockCanvas
      let ctx = canvas.getContext("2d");
      let [x0, y0] = [this.canvas.width / 2, this.canvas.height / 2]; //获取圆心x,y
      this.L = this.canvas.width / 2 - 10; //设置圆半径
      let [hourMaxL, hourMinL] = [this.L-2, this.L - 48]; //获取时刻度首位距离x0,y0位置
      let [minMaxL, minMinL] = [this.L - 2, this.L - 15];
      ctx.clearRect(0, 0, canvas.width, canvas.height); //清除画布
      this.drawHoursScale(ctx, x0, y0, 50, 3, hourMaxL, hourMinL); //绘制表盘的时钟刻度scale
      this.drawMinsScale(ctx, x0, y0, 60, 3, minMaxL, minMinL); //绘制表盘分钟刻度
    },
    drawHoursScale(ctx, x0, y0, scaleNum, scaleW, maxL, minL) {
      for (let i = 0; i < 720; i++) {
        let angel = -90 + i * (360 / 720); //角度
        let [x1, y1] = [
          x0 + Math.cos((angel * Math.PI) / 180) * maxL,
          y0 + Math.sin((angel * Math.PI) / 180) * maxL
        ];
        let [x2, y2] = [
          x0 + Math.cos((angel * Math.PI) / 180) * minL,
          y0 + Math.sin((angel * Math.PI) / 180) * minL
        ];
        /*  */
        ctx.strokeStyle = "#444";
        if (i == 23 || i == 33 || (i > 94 && i < 139)) {
          ctx.strokeStyle = "yellow";
        } /*  */
        ctx.save();
        ctx.beginPath();
        ctx.lineWidth = scaleW;
        ctx.lineCap = "round";
        ctx.moveTo(x1, y1);
        ctx.lineTo(x2, y2);
        ctx.stroke();
        ctx.closePath();
        ctx.restore();
      }
    },
     drawMinsScale(ctx, x0, y0, scaleNum, scaleW, maxL, minL) {
      for (let i = 0; i < 720; i++) {
        let angel = -90 + i * (360 / 720); //角度
        let [x1, y1] = [
          x0 + Math.cos((angel * Math.PI) / 180) * maxL,
          y0 + Math.sin((angel * Math.PI) / 180) * maxL
        ];
        let [x2, y2] = [
          x0 + Math.cos((angel * Math.PI) / 180) * minL,
          y0 + Math.sin((angel * Math.PI) / 180) * minL
        ];
        /*  */
        ctx.strokeStyle = "red";
        if (i == 23 || i == 33 || (i > 34 && i < 99)) {
          ctx.strokeStyle = "blue";
        } /*  */
        ctx.save();
        ctx.beginPath();
        ctx.lineWidth = scaleW;
        ctx.lineCap = "round";
        ctx.moveTo(x1, y1);
        ctx.lineTo(x2, y2);
        ctx.stroke();
        ctx.closePath();
        ctx.restore();
      }
    }
  }
};
</script>
<style lang="scss" scoped>
@import "@/styles/global.scss";
#coolClockWrap {
  display: flex;
  flex-flow: row nowrap;
  justify-content: center;
  align-items: center;
  width: vw(830);
  height: vh(830);
  background: #1d1d1d;
}
</style>