<template>
  <div class="Waterfall wf-content">
    <!-- 如果不用wf-content？ -->
    <!-- 遍历图片数组获取图片 -->
    <div class="wf-item mask" v-for="(item, index) in imgList" :key="index">
      <img v-if="$store.state.choose !== 2" v-lazy="item" alt="xxx" ref="image" @load="imageOnload()" />
    
    </div>
  </div>
</template>

<script>
// import axios from 'axios'
import { WaterFall } from "@/waterfall/waterfall"; //js那边不是export default默认导出,所以这里要用花括号，不然获取不到

function importAll(r) {
  //导入多个模块
  return r.keys().map(function (key) {
    return r(key); //webpack提供的r方法,返回上下文(context)接口的函数。将每个模块都通过r(key)导入进来,将获取的相对路径作为参数传递给 r 函数，并返回导入的模块对象
  });
}

// 杜震
export default {
  name: "LocalImg",
  data() {
    return {
      imgList: [],
      // type: "recommend", //tab中选择的图片分类
      firstRowNums: 0,
      firstRowImgsHeight: [],
      columns: 4,
      timmer: null,

    };
  },
  created() {
    //默认选第一个tab
    this.photoShow(0);
  },
  mounted() {
    // 监听窗口大小变化事件，并实时更新数据属性中的宽度和高度值
    // window.addEventListener('resize', this.imageOnload);
    window.onresize = () => {
      clearTimeout(this.timmer);
      setTimeout(() => {
        this.imageOnload();
      }, 600);
    };
  },
  methods: {
    imageOnload() {
      //加载图片 根据浏览器宽度决定列数

      if (window.innerWidth <= 500) {
        this.columns = 2;
      } else if (window.innerWidth < 1000) {
        this.columns = 3;
      } else if (window.innerWidth < 1500) {
        this.columns = 3;
      } else if (window.innerWidth < 2000) {
        this.columns = 5;
      }

      
      new WaterFall({
        //执行waterfall.js文件中的构造函数
        el: ".wf-content",
        column: this.columns,
        gap: 23, //间距  单位px
      });
    },

    photoShow(choose) {
      //根据选择的tab 切换图片类型
      switch (choose) {
        case 0:
          this.imgList = null;

          // 网络图片(调用json文件)
          fetch('/2023.json')
            .then(response => response.json())
            .then(data => {
              // 将解析得到的链接列表赋值给 imgList 变量
              this.imgList = data;
            })
            .catch(error => {
              console.error('加载 图片json 文件时出错:', error);
            });
          break;

        case 1:
          this.imgList = null;
          fetch('/2022.json')
            .then(response => response.json())
            .then(data => {
              // 将解析得到的链接列表赋值给 imgList 变量
              this.imgList = data;
            })
            .catch(error => {
              console.error('加载 图片json 文件时出错:', error);
            });
 
          case 2:
          this.imgList = null;
          fetch('/2022.json')
            .then(response => response.json())
            .then(data => {
              // 将解析得到的链接列表赋值给 imgList 变量
              this.imgList = data;
            })
            .catch(error => {
              console.error('加载 图片json 文件时出错:', error);
            });

            case 3:
          this.imgList = null;
          fetch('/2022.json')
            .then(response => response.json())
            .then(data => {
              // 将解析得到的链接列表赋值给 imgList 变量
              this.imgList = data;
            })
            .catch(error => {
              console.error('加载 图片json 文件时出错:', error);
            });

            case 4:
          this.imgList = null;
          fetch('/2022.json')
            .then(response => response.json())
            .then(data => {
              // 将解析得到的链接列表赋值给 imgList 变量
              this.imgList = data;
            })
            .catch(error => {
              console.error('加载 图片json 文件时出错:', error);
            });

            case 5:
          this.imgList = null;
          fetch('/2022.json')
            .then(response => response.json())
            .then(data => {
              // 将解析得到的链接列表赋值给 imgList 变量
              this.imgList = data;
            })
            .catch(error => {
              console.error('加载 图片json 文件时出错:', error);
            });

            case 6:
          this.imgList = null;
          fetch('/2022.json')
            .then(response => response.json())
            .then(data => {
              // 将解析得到的链接列表赋值给 imgList 变量
              this.imgList = data;
            })
            .catch(error => {
              console.error('加载 图片json 文件时出错:', error);
            });

        default:
          break;
      }
    },
  },
  watch: {
    "$store.state.choose"(newVal) {
      //切换tab的新值
      this.photoShow(newVal);
    },
  },
};

/* 本地图片
this.imgList = importAll(
  require.context(
    "@/assets/imgs/recommend",
    false,
    /\.(png|jpe?g|svg)$/
  )
);

网络图片 (直接调用网络图片的URL,但是很代码会很长，不建议)
          this.imgList = [
  "https://cdn.jsdelivr.net/gh/Lovirr/cdn/IMAGE/202307061025451.webp",
  "https://cdn.jsdelivr.net/gh/Lovirr/cdn/IMAGE/202307061021397.png",
  "https://cdn.jsdelivr.net/gh/Lovirr/cdn/IMAGE/202307051240713.webp",
  "https://cdn.jsdelivr.net/gh/Lovirr/cdn/IMAGE/202307051240716.webp"
  // 添加更多网络图片的URL
]; */



/*         case 2:
          this.imgList = null;
          this.imgList = importAll(
            require.context("@/assets/video", false, /\.(mp4)$/)
          );
          break;
        case 3:
          this.imgList = null;
          this.imgList = importAll(
            require.context("@/assets/imgs/game", false, /\.(png|jpe?g|svg)$/)
          );
          break;
        case 4:
          this.imgList = null;
          this.imgList = importAll(
            require.context("@/assets/imgs/pet", false, /\.(png|jpe?g|svg)$/)
          );
          break; */

</script>

<style lang="less">
* {
  margin: 0;
  padding: 0;
}

.Waterfall {
  position: relative;
  margin: 0px auto 0px;
  width: 85%;

  .wf-item {
    position: absolute;


    img {
      width: 100%;
      border-radius: 10px;
      vertical-align: bottom;
      /*去除图片下方的空隙*/
    }

  }


/*   .wf-item{
    transition: all 0.45s ease-in-out;
  }
  .wf-item:hover {
    transform: scale(0.95) rotate(2deg);

    // cursor: pointer;
  } */

}



</style>


