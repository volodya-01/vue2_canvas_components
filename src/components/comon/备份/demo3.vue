<template>
  <div id="coolClockWrap" ref="coolClockWrapbox">
    <canvas ref="coolClockCanvas" :width="canvas.width" :height="canvas.height"></canvas>
  </div>
</template>

<script>
var elementResizeDetectorMaker = require("element-resize-detector")
export default {
  name: "",
  data() {
    return {
      canvas: {
        width: 630,
        height: 830
      },
      L: 0 //基础半径
    };
  },
  mounted() {
      this.resizefun()
    /* this.drawCoolClock(); */
  },
  destroyed() {},
  methods: {
      //自适应方法
      resizefun(){
          var erd = elementResizeDetectorMaker()
    erd.listenTo(this.$refs.coolClockWrapbox,  element=> {
      var width = element.offsetWidth
      var height = element.offsetHeight
       this.canvas.width= width*0.4,
       
       this.canvas.height= height*0.8
     
      this.$nextTick( ()=> {
        console.log("Size: " + width + "x" + height)
        //使canvas尺寸重置
        this.drawCoolClock();
       
      })
    })
      },
    drawCoolClock() {
      let canvas = this.$refs.coolClockCanvas;
      let ctx = canvas.getContext("2d");
      let [x0, y0] = [this.canvas.width / 2, this.canvas.height / 2]; //获取圆心x,y
      this.L = this.canvas.width / 2 - 30; //设置圆半径
      let [MaxL1, MinL1] = [this.L - 2, this.L]; //获取第1圈首位距离x0,y0位置
      let [MaxL2, MinL2] = [this.L - 2, this.L - 10]; //获取第2圈首位距离x0,y0位置
      let [MaxL3, MinL3] = [this.L - 2, this.L-20]; //获取第3圈首位距离x0,y0位置
      let [MaxL4, MinL4] = [this.L - 2, this.L-25]; //获取第4圈首位距离x0,y0位置
      let [MaxL5, MinL5] = [this.L - 2, this.L-50]; //获取第5圈首位距离x0,y0位置
      let [MaxL6, MinL6] = [this.L - 2, this.L - 55]; //获取第6圈首位距离x0,y0位置
      let [MaxL7, MinL7] = [this.L - 2, this.L - 60]; //获取第7圈首位距离x0,y0位置
      let [MaxL8, MinL8] = [this.L - 2, this.L - 80]; //获取第8圈首位距离x0,y0位置
      let [MaxL9, MinL9] = [this.L - 2, this.L - 85]; //获取第9圈首位距离x0,y0位置
      let [MaxL10, MinL10] = [this.L - 2, this.L - 90]; //获取第10圈首位距离x0,y0位置
      let [MaxL11, MinL11] = [this.L - 2, this.L - 100]; //获取第11圈首位距离x0,y0位置
      let [MaxL12, MinL12] = [this.L - 2, this.L - 105]; //获取第12圈首位距离x0,y0位置
      let [MaxL13, MinL13] = [this.L - 2, this.L - 125]; //获取第13圈首位距离x0,y0位置
      let [MaxL14, MinL14] = [this.L - 2, this.L - 132]; //获取第14圈首位距离x0,y0位置
      let [MaxL15, MinL15] = [this.L - 2, this.L - 138]; //获取第15圈首位距离x0,y0位置
      let [MaxL16, MinL16] = [this.L - 2, this.L - 195]; //获取第16圈首位距离x0,y0位置
   
      ctx.clearRect(0, 0, canvas.width, canvas.height); //清除画布
    
      this.drawScale16(ctx, x0, y0, 50, 3, MaxL16, MinL16); //绘制表盘第16圈
      this.drawScale15(ctx, x0, y0, 50, 3, MaxL15, MinL15); //绘制表盘第15圈
      this.drawScale14(ctx, x0, y0, 50, 3, MaxL14, MinL14); //绘制表盘第14圈
      this.drawScale13(ctx, x0, y0, 50, 3, MaxL13, MinL13); //绘制表盘第13圈
      this.drawScale12(ctx, x0, y0, 50, 3, MaxL12, MinL12); //绘制表盘的第12圈
      this.drawScale11(ctx, x0, y0, 50, 3, MaxL11, MinL11); //绘制表盘的第11圈
      this.drawScale14(ctx, x0, y0, 50, 3, MaxL10, MinL10); //绘制表盘的第10圈
       this.drawScale15(ctx, x0, y0, 50, 3, MaxL9, MinL9); //绘制表盘第9圈
         this.drawScale14(ctx, x0, y0, 50, 3, MaxL8, MinL8); //绘制表盘的第8圈
           this.drawScale15(ctx, x0, y0, 50, 3, MaxL7, MinL7); //绘制表盘第7圈
            this.drawScale14(ctx, x0, y0, 50, 3, MaxL6, MinL6); //绘制表盘的第6圈
            this.drawScale11(ctx, x0, y0, 50, 3, MaxL5, MinL5); //绘制表盘的第5圈
         this.drawScale14(ctx, x0, y0, 50, 3, MaxL4, MinL4); //绘制表盘的第4圈
            this.drawScale11(ctx, x0, y0, 50, 3, MaxL3, MinL3); //绘制表盘的第3圈

 this.drawScale14(ctx, x0, y0, 50, 3, MaxL2, MinL2); //绘制表盘的第2圈
 this.drawScale15(ctx, x0, y0, 50, 3, MaxL1, MinL1); //绘制表盘的第1圈
 
    },
       
    drawScale1(ctx, x0, y0, scaleNum, scaleW, maxL, minL) {
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
        ctx.strokeStyle = "orange";
        if (i == 23 || i == 33 || (i > 34 && i < 99)) {
          ctx.strokeStyle = "green";
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
    drawScale2(ctx, x0, y0, scaleNum, scaleW, maxL, minL) {
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
     drawScale11(ctx, x0, y0, scaleNum, scaleW, maxL, minL) {
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
        ctx.strokeStyle = "#292934";
        if (i %2==0) {
          ctx.strokeStyle = "#245274";
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
      drawScale12(ctx, x0, y0, scaleNum, scaleW, maxL, minL) {
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
        ctx.strokeStyle = "#292934";
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
    drawScale13(ctx, x0, y0, scaleNum, scaleW, maxL, minL) {
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
        //
        ctx.strokeStyle = "#292934";
        if (i >0&&i<99) {
          ctx.strokeStyle = "#836B27";
        } else if (i >103&&i<359) {
          ctx.strokeStyle = "#4CC2CE";
        } else if (i >369&&i<712) {
          ctx.strokeStyle = "rgb(108,40,46)";
        }else{
            ctx.strokeStyle = "#292934";
        }
        //
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
    drawScale14(ctx, x0, y0, scaleNum, scaleW, maxL, minL) {
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
        ctx.strokeStyle = "#292934";
        /*  */
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
    drawScale15(ctx, x0, y0, scaleNum, scaleW, maxL, minL) {
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
        ctx.strokeStyle = "#343F4A";
        /*  */
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
    drawScale16(ctx, x0, y0, scaleNum, scaleW, maxL, minL) {
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
        ctx.save();
        ctx.beginPath();
        ctx.lineWidth = scaleW;
        ctx.lineCap = "round";
        ctx.moveTo(x1, y1);
        ctx.lineTo(x2, y2);
        ctx.stroke();
        ctx.arc(x0, y0, maxL, minL, Math.PI * 2, true);
        ctx.closePath();
        ctx.fillStyle = "#292934"; //填充圆
        ctx.fill();
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
  width: vw(1030);
  height: vh(1630);
  background: #1b1b1b;
}
</style>