<template>
  <div class="tab-bar-item" @click="itemClick">
    <slot v-if="!isActived" name="slot-img">

    </slot>
    <slot v-else name="slot-active-img"></slot>
    <div :style="activeStyle">
      <slot name="slot-text" ></slot>
    </div>
<!--    具名slot-->
<!--    <div>首页</div>-->

  </div>
</template>

<script>
export default {
name: "tab-bar-item",
  data(){
  return{
    // isActived:false
  }
  },
  computed:{
  isActived(){
    return this.$route.path.indexOf(this.path)!==-1
  },
    activeStyle(){
    return this.isActived?{color:this.activeColor}:{}  //三目运算符
    }
  },
  props:{
     path:String, //传过来的路径，用于跳转，用于路由
    activeColor:{
       type:String,
      default:'deepSkyblue'
    }
  },
  methods:{
     itemClick(){
    // console.log('kkk')
       // console.log(this.path)
       // console.log(this.$route)
    this.$router.push(this.path)
       //通过代码跳转路由
  }
  }
}
</script>

<style scoped>
.tab-bar-item{
  text-align: center;
  height: 49px;
  /*移动端导航的固定像素，一般都是49px*/
}

</style>
