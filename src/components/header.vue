<template>
  <header>
      <h3>{{title}}</h3>
      <ul>
        <li>
           <router-link to="/" >Currencies List</router-link> 
        </li>
        <li>
            <router-link to="/convert">Convert Currencies</router-link> 
        </li>
      </ul>

  </header>
</template>

<script>
export default {
  data () {
   return{
      title: "CUR VER"
   }
  }
}
</script>

<style scoped>
  header{
    width: 100%;
    background-color:#444;
    height: 50px;
    text-align: center;
    color:#fff;
    padding: 0px;
    margin:0px;
  }
  h3{
    margin:0px;
    padding:10px;
    width: 20%;
    float: left;
  }
  ul{
    list-style: none;
    width: 60%;
    float: right;
  }
  li{
    display: inline;
    padding: 10px;
  }
  a{
    color: #fff;
    text-decoration: none;
  }


</style>
