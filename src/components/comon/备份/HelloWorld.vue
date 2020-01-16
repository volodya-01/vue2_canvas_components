<template>
  <div class="hello">
    <div class="demooutbox">
      <div  class="demo1box" >
        <div class="fontstyle">一、基础图形</div>
        <demo1/>
      </div>
      <div class="demo1box">
        <div class="fontstyle">二、最外圈加数字</div>
        <demo2 />
      </div>
      <div class="demo1box">
         <div class="fontstyle">三、白天夜间外圈分别加数字</div>
        <demo3 />
      </div>
      <div class="demo1box">
          <div class="fontstyle">四、最外圈加图片</div>
        <demo4 />
      </div>
    </div>
  </div>
</template>

<script>
import demo1 from "./comon/demo1";
import demo2 from "./comon/demo2";
import demo3 from "./comon/demo3";
import demo4 from "./comon/demo4";

export default {
  name: "HelloWorld",
  components: {
    demo1,
    demo2,
    demo3,
    demo4
  },
  data() {
    return {};
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
@import "@/styles/global.scss";
.hello {
  display: flex;
  flex-flow: column;
  justify-content: flex-start;
  align-items: center;
  width: vw(1920);
  height: vh(1080);
  .demooutbox {
    margin-top: 30px;
    .demo1box {
      margin-top: 60px;
      .fontstyle{
        color: seagreen;
        font: 400 vh(36) "微软雅黑";
        margin-bottom: vh(20);
      }
    }
  }
}
</style>
