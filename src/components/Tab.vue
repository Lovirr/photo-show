<template>
  <div class="tab">
    <!-- $el 是这里的整个dom -->
    <li class="tab-item li" @click="chooseTab($el, index)" v-for="(item, index) in $store.state.tabList">
      {{ item }}
    </li>
  </div>
</template>

<script>
export default {
  name: "Tab",
  components: {},
  props: {},
  data() {
    return {};
  },
  watch: {},
  computed: {},
  methods: {
    chooseTab(tabDom, index) { //选择类型
      for (let i = 0; i < tabDom.childNodes.length; i++) {
        i === index ? tabDom.childNodes[index].className = 'tab-item-active li' : tabDom.childNodes[i].className = 'tab-item li'
        this.$store.state.choose = index
      }
    },
    changeLiSize() {
      var tabDom = document.getElementsByClassName('li')
      for (let i = 0; i < tabDom.length; i++) {
        // window.innerWidth < 650 ?   //屏幕宽度小于650px 时 切换小字体 否则放大
        //     tabDom[i].style.fontSize = '10px' :
        //     tabDom[i].style.fontSize = '20px'
      }
    }
  },
  created() {

  },
  mounted() {
    var tabDom = document.getElementsByClassName('li')
    tabDom[this.$store.state.choose].className = 'tab-item-active li'//默认选中第一个
    this.changeLiSize()
    window.addEventListener('resize', this.changeLiSize);
  }
};
</script>
<style lang="less" scoped>
.tab { //选择栏
  width: 100%;
  min-height: 111px;
  display: flex;
  justify-content: center;
  align-items: center;
  // flex-wrap: wrap;
  // margin: 10px;
  gap: 40px;
  // background: #141414;

  .li {
    width: 120px;
    list-style: none;
    font-weight: bold;
    font-size: large;
    cursor: pointer;
    padding: 10px;
    box-sizing: border-box;
    border-radius: 23px;
    background: #141414;
  }

  .tab-item {
    text-align: center;
    color: rgb(66, 63, 63);
    background: rgb(219, 223, 227);
    transition: all 0.45s;
  }

  .tab-item:hover {
    text-align: center;
    color: white;
    background-color: rgb(38, 39, 40);
  }


  .tab-item-active {
    text-align: center;
    color: white;
    background-color: rgb(38, 39, 40);
  }
}
</style>