<template>
  <div id="app"
        ref="app_main">
    <headerNav @activeBlockAdder="getDataWithHeader"/>
    <div id="Main">
      <SideNav @act="act"/>
      <MainComp :isActiveTitle="isActiveT"
                :actSide="actSide"/>
    </div>
    
  </div>
</template>

<script>
import headerNav from './components/header.vue'
import SideNav from './components/side.vue'
import MainComp from './components/main.vue'

export default {
  name: 'App',
  components: {
    headerNav,
    SideNav,
    MainComp,
  },
  data(){
    return{
      isActiveT: "",
      actSide:{}
    }
  },
  methods:{
    act(activeSide){
      this.actSide = activeSide
      console.log();
    },
    getDataWithHeader(Active)
    {
      this.isActiveT = Active
      console.log(this.isActiveT);
    }
  }
}
</script>

<style>
*
{
  margin: 0;
  padding: 0;
}
:root
{
  --backgroundBlockDop: #804ab5;
  --textInBlockDop: #ffffff;
  --textMain: #000;
  --backgroundBlock: #fff;
  --backgroundBlockHover: #7fb54a;
  --lineHover: #7fb54a;
}
.dark
{
  --backgroundBlockDop: #321f44;
  --textInBlockDop: #c0c0c0;
  --textMain: #d5d5d5;
  --backgroundBlock: rgb(41, 41, 41);
  --backgroundBlockHover: #5e8537;
  --lineHover: #577c31;

}
ul
{
  list-style-type: none;
}
#app {
  transition: all .4s ease;
  font-family:'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  
}
#Main{display: flex; }
body
{
  overflow:hidden;
}
</style>
