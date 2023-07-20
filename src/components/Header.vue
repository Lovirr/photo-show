<template>
  <!-- 顶部导航栏 -->
  <div class="header">
    <img class="homevideo" src="https://cdn.jsdelivr.net/gh/Lovirr/cdn/IMAGE/a320.webp">
    <div class="topmiddle">
      <h1 ref="h1">欢迎来到 <br />小骆同学的摄影展</h1>
    </div>
  </div>
</template>

<script></script>
  
<style lang="less">
* {
  margin: 0;
  padding: 0;
}

.header {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100vh;
  overflow: hidden;
  text-align: center;
  background-color: #141414;

  .homevideo {
    display: block;
    position: absolute;
    // left: 0%;
    // top: 50%;
    // transform: translate(-50%, -70%);
    // min-width: 100%; //拉伸收缩页面 改变分辨率，视频都铺满父级div
    max-width: 100%;
  }

  .topmiddle {
    z-index: 1;
    flex: 1;
    max-width: 900px;
    padding: 0 15px;

    h1 {
      pointer-events: none;
      color: white;
      font-weight: bold;
      font-size: 7vw;
      // margin-bottom: 20px;
      text-align: center;
      font-family: "PingFang SC", "Microsoft YaHei", sans-serif;
      animation: fade-in-up 1s ease-out both;
    }

  }

  @keyframes fade-in-up {
    from {
      opacity: 0;
      transform: translateY(200px);
    }

    to {
      opacity: 1;
      transform: translateY(0);
    }
  }




}
</style>