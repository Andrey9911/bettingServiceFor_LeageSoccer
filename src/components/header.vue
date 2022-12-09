<template>
  <div class="header_nav">
    <div id="logo">
      <img src="../assets/logo.png" alt="" width="100px">
    </div>
    <div class="added"
        @click="add">
      <svg xmlns="http://www.w3.org/2000/svg" width="35" height="35" fill="currentColor" class="icon bi bi-plus" viewBox="0 0 16 16">
        <path d="M8 4a.5.5 0 0 1 .5.5v3h3a.5.5 0 0 1 0 1h-3v3a.5.5 0 0 1-1 0v-3h-3a.5.5 0 0 1 0-1h3v-3A.5.5 0 0 1 8 4z"/>
      </svg>
    </div>
    <div class="dark_icon"
        @click="dark"
        ref="dark">
      <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" fill="currentColor" class="icon bi bi-moon-fill" viewBox="0 0 16 16">
          <path d="M6 .278a.768.768 0 0 1 .08.858 7.208 7.208 0 0 0-.878 3.46c0 4.021 3.278 7.277 7.318 7.277.527 0 1.04-.055 1.533-.16a.787.787 0 0 1 .81.316.733.733 0 0 1-.031.893A8.349 8.349 0 0 1 8.344 16C3.734 16 0 12.286 0 7.71 0 4.266 2.114 1.312 5.124.06A.752.752 0 0 1 6 .278z"/>
      </svg>
    </div>
    <div class="ignore"><App/></div>
    
  </div>
</template>

<script>
import App from '../App.vue' 


export default {
  name: 'headerNav',
  components:{
    App,
    
  },
  data(){
    return{
      activeBlockAdd: false
    }
    
  },
  methods:{
    dark()
    {
      console.log();
    },
    add()
    {
      if(!this.activeBlockAdd) this.activeBlockAdd = true
      else this.activeBlockAdd = false
      
      this.$emit("activeBlockAdder",this.activeBlockAdd)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.header_nav
{
  align-items: center;
  padding: 10px 30px;
  display: flex;
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  box-shadow: 0px 5px 10px 2px #223c5033;  
  box-sizing: border-box;
  width: 100%;
  height: 65px;
  background-color: var(--backgroundBlockDop);
  color: var(--textInBlockDop);
}
.added
{
  margin-left:80%;
  background-color: #a9a9a96a;
  height: fit-content;
  width: fit-content;
  padding: 2px;
  border-radius: 7px;
}
.dark_icon
{
  margin: 0 10px;
  box-sizing: border-box;
  background-color: #a9a9a96a;
  height: fit-content;
  width: fit-content;
  padding: 10px;
  border-radius: 7px;
}
.added:hover,.dark_icon:hover{color: var(--lineHover); transition: all .1s ease; cursor: pointer;}
#logo
{
  width: fit-content;
}
.ignore{display: none;}
</style>

