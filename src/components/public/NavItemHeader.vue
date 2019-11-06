<template>
  <div>
    <section class="nav-items" v-if="!this.show">
        <ul class="item-list">
          <li class="item"
            v-for="(item,index) in itemList"
            :to="item.path"
            :class="{active:currentIndex==index}"
            @click="changeSelect(index)"
            :key="index"
          >{{item.name}}</li>
        </ul>
        <div class="item-more" >
          <i class="fa fa-chevron-down"></i>
        </div>
    </section>
    
  </div>

</template>

<script>
export default {
    name: "NavItemHeader",
    props:["itemList"],
    data(){
      return{
        show:false,
        currentIndex:0
      }
    },
  methods:{
    changeSelect(index){
      //点击切换成选中的样式，把变量的值赋值为 index
       this.currentIndex=index;
    },
    open(){
      this.show=true;
    },
    close(){
      this.show=false
    }
  }
}
</script>

<style scoped>
  /* @import "../../../static/theme/1/yuanjng.css"; */
  
*{
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
.nav-items {
  display: flex;
  background-image: linear-gradient(90deg,#0af,#0085ff);
  position: fixed;
  top: 0;
  width: 100%;
  z-index: 10;
}
/*右侧下拉箭头*/
.item-more{
  width:3.6rem;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 3rem;
  color: #fff;
  font-size: 1rem;
}
/*左侧ul列表*/
.item-list {
  flex:1;
  overflow-x: scroll;
  white-space: nowrap;
  height: 3rem;
  padding-left: 1rem;
  padding-bottom: 2rem;
}
/*列表中的每一项*/
.item-list>.item {
  display: inline-block;
  margin-right: 7.466667vw;
  padding: 1rem 0 .36rem;
  font-size: 0.9rem;
  font-weight: 900;
  color: #fff;
  opacity: .7;
}
/*如果被选中的样式*/
.item-list > .active {
  border-bottom: .1rem solid #fff;
  opacity: 1;
}
/*弹出层*/
.filter-category{
  position: absolute;
  top:0;
  left:0;
  width: 100%;
  z-index: 100000;
}
/*头部*/
.filter-category .top{
  display: flex;
  width: 100%;
  z-index: 11;
  color: #666;
}
/*关闭按钮*/
.filter-category .top .close{
  width:3.6rem;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 3rem;
  color: #666666;
  font-size: 1rem;
}
  /*头部标题*/
.filter-category .top .title {
  flex:1;
  height: 3rem;
  padding-left: 1rem;
  padding-bottom: 2rem;
  line-height: 3rem;
  color: #333;
  font-size: 0.9rem;
  font-weight: 900;
}
/*内容区域*/
.filter-scroller {
  display: flex;
  height: 100%;
  border-top: 1px solid #eee;
  background-color: #fff;
}
  /*左侧导航*/
.main-menu{
  width: 9rem;
  background-color: #fcfcfc;
}
/*li的每一项*/
.menu-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height:3rem ;
  line-height: 3rem;

}
/*左侧*/
.menu-item--main{
  padding-right:.8rem;
  border-right: 1px solid #f5f5f5;
  border-bottom: .04em solid transparent;
}
/*name*/
.menu-name {
  font-size: 0.9rem;
  flex: 1;
  height: 1.5rem;
  line-height: 1.5rem;
  color: #666;
}
.menu-item--main .menu-name{
  position: relative;
  padding-left: 1.533333rem;
}
.count {
  position: relative;
  width: 2.4rem;
  height: 1rem;
  font-size: .6rem;
  border: 1px solid #eee;
  border-radius: .6rem;
  color: #999;
  display: flex;
  justify-content: center;
  align-items: center;
}
/*右侧*/
.submenu {
  flex: 1;
  padding: 0 1rem 0 1.5rem;
  background: #fff;
}
/*图片*/
.submenu img{
  margin-right: 1rem;
  width: 2.8rem;
  height: 2.8rem;
  vertical-align: middle;
}






</style>
