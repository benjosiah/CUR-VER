<template>
    <div id="list" >
        <div id="wrap">
            <h1>Currency Converter</h1>
            <form action="">
                <label for=""> From</label>
                <div>
                    <select name="" id="" v-model="from">
                        <option v-bind:value="list.code" v-for="list in totalLists" > {{list.code}} </option>
                    </select>
                </div>
                <label for="">To</label>
                <div>
                    <select name="" id="" v-model="to">
                        <option v-bind:value="list.code" v-for="list in totalLists" > {{list.code}} </option>
                    </select>
                </div>
                <label for="">Amount</label>
                <div>
                    <input type="text" v-model="amount">
                </div>
                <div>
                    <button v-on:click.prevent="convert">Convert</button>
                </div>
               
            </form>
            <div id="display" >
               <p v-show="show">From: {{query.form}}</p>
               <p v-show="show">TO: {{query.to}} </p>
               <p v-show="show">Amount: {{query.amount}}</p>
               <p v-show="show">Rate: {{result.value}} </p>
            </div>

        </div>
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
       from:"",
       to:"",
       amount:"",
       query:{},
       result:{},
       show:false

    
    } 
  },
  methods:{
        convert:function(){
            this.$http.get("https://currency28.p.rapidapi.com/convert-currency?amount="+this.amount+"&to="+this.to+
            "&from="+this.from,
                {
                    headers: {
                        "x-rapidapi-host": "currency28.p.rapidapi.com",
                        "x-rapidapi-key": "fc8b90294fmsh197d8e5cd91cab8p1ed5a3jsn664ee7c50af3"
                    }
                }).then(function(data){
                    data.body.query=this.query
                    data.body.result=this.result
                    console.log(data.body.result=this.result)
                    dispatchEvent
                    this.show=true
                }
            )
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
        min-height: 456px;
    }
  #wrap{
    width: 60%;
    text-align: center;
    margin: auto;
    background-color: rgb(22, 9, 53);
    color: white;
    min-height: 450px;
  }
  select, input{
      width: 200px;
      background-color: blueviolet;
  }
  h1{
      margin-top:0px;
      padding: 20px;
  }
  form div{
      padding: 10px;
  }
  button{
      width: 70px;
      height: 30px;
      background-color: rgb(78, 78, 167);
  }
  #display{
      width: 40%;
      height: 100px;
      background-color: rgb(220, 120, 250);
      margin: auto;
      overflow-y: scroll;
      overflow-anchor:unset;
  }

 
</style>
