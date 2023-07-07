<template>
  <div>
    <a href="#" id="gotoTop"><img src="../assets/icons/热门.png" alt=""></a>
  </div>
</template>

<script>
// 滚动条不隐藏的情况实现不可滚动
var winX = null;
var winY = null;

window.addEventListener('scroll', function () {
  if (winX !== null && winY !== null) {
    window.scrollTo(winX, winY);
  }
  // 判断当前浏览器视口高度 显示与隐藏 "回到顶部" 按钮
  window.scrollY > 500 ?
    this.document.getElementById('gotoTop').style.visibility = 'visible' :
    this.document.getElementById('gotoTop').style.visibility = 'hidden'
});

function disableWindowScroll() {
  winX = window.scrollX;
  winY = window.scrollY;
}

function enableWindowScroll() {
  winX = null;
  winY = null;
}

</script>
<style lang="less" scoped>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

.back {
  z-index: 2;
  visibility: hidden;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, .5);


}

#gotoTop {
  visibility: hidden;
  z-index: 1;
  position: fixed;
  bottom: 30px;
  right: 20px;
  width: 40px;
  height: 40px;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 50%;
  background-color: #fff;
  box-shadow: 0px 0px 8px 0px rgba(0, 0, 0, .4);

  img {
    transform: rotate(180deg);
  }
}</style>