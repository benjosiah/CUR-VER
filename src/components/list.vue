<template>
    <div id="list" >
        {{key}}
        <ul>
            <li v-for="list in totalLists.slice(value,ValueEnd)">
                <h3>{{list.code}}</h3>
                <h5>{{list.name}}</h5>
            </li>
        </ul>
        <button v-show="showprev" v-on:click.prevent="prev">Previous</button>
        <button v-show="shownext" v-on:click.prevent="next">Next</button>

    </div>
</template>

<script>
export default {
    props:{
        totalLists:{
            type:Array,
        }
    },
  data () {
        return{
            lists:[],
            value:0,
            ValueEnd:30,
            showprev:false,
            shownext:true,
            key:process.env.VUE_APP_API_KEY
        } 
    },
  methods:{
    next: function() {
        this.value=this.value+30;
        this.ValueEnd=this.ValueEnd+30;
        this.showprev=true;
        if(this.totalLists.slice(this.value,this.ValueEnd).length<30){
            this.shownext=false
        }
    },
    prev: function(){
       this.value=this.value-30;
        this.ValueEnd=this.ValueEnd-30;
        this.shownext=true;
        this.lists=this.totalLists.slice(this.value,this.ValueEnd)
        if (this.value==0) {
            this.showprev=false
        }
        
    }
    
  }

  
  
}
</script>

<style scoped>
  #list{
    width: 100%;
    padding:0px 20px;
    margin:40px auto;
    box-sizing:border-box;
    min-height: 480px;
  }
 ul{
    display:flex;
    flex-wrap:wrap;
    list-style: none;
    padding:0px;
 }
 li{
     flex-grow:1;
     flex-basis:300px;
     padding:30px;
     border:1px solid #222;
     text-align:center;
     color:#fff;
     background-color: rgb(22, 9, 53);
     margin: 10px;
 }

</style>
