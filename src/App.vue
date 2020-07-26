<template>
  <div>
    <app-header></app-header>
    <router-view v-bind:totalLists="totalLists" v-bind:lists="lists" ></router-view>
    <app-footer></app-footer>


  </div>
</template>

<script>
import Header from "./components/header.vue";
import Footer from "./components/footer.vue";
import List from "./components/list.vue";
import Convert from "./components/convert.vue";
export default { 
 components:{
   "app-header": Header,
   "app-footer": Footer,
   "convert": Convert

 },
  data () {
    return {
      lists:[],
      totalLists:[],
      
      
    }
  },
  created(){
    
  this.$http.get('https://currency28.p.rapidapi.com/all-currency',
      {headers: {
          "x-rapidapi-host": "currency28.p.rapidapi.com",
          "x-rapidapi-key": "fc8b90294fmsh197d8e5cd91cab8p1ed5a3jsn664ee7c50af3"
          
      }}).then(function (data) {
          this.totalLists=data.body.result;
          this.lists=data.body.result
          console.log(data)
      })
},
  mounted(){
    console.log(process.env.VUE_APP_NOT_SECRET_CODE)
  }
}
</script>

<style>
body{
  margin:0px;
  padding:0px;
  background-color: rgb(112, 88, 168);
}
div{
  padding: 0px;
  width:100%;
  margin:0px;
}

</style>
