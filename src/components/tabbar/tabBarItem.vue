<template>
  <div class="tab-bar-item" @click="itemClick">
    <div :style="activeStyle">
    <slot name="item-text"></slot>
    </div>

  </div>
</template>

<script>
export default {
  name:"TabBarItem",
  props:{
    path:String,
    activeColor:{
      type:String,
      default:'blue'
    }
  },
  data(){
    return{
      // isActive:true
    }
  },


  computed:{
    isActive(){
      // return this.$route.path.indexOf(this.path) !== -1
      return this.$route.path == this.path
    },
    activeStyle(){
      return this.isActive ? {color:this.activeColor} :{}
    }
  },
  methods:{
    itemClick(){
      this.$router.replace(this.path)
    }
  }
}
</script>

<style>
  .tab-bar-item{
    flex:1;
    text-align: center;
    height:49px;
  }

</style>
