<template>
    <div id="app" class="container">
      <div class="grid">
        <div class="input-num">
           {{result|| 0}}
        </div>
        <button v-on:click="input(num)" class="number btn" v-for="num in numbers">{{num}}</button>
        <button v-on:click="input(oper)" class="oper btn" v-for="oper in operations">{{oper}}</button>
        <button v-on:click="reset()" class="number btn">C</button>
        <button v-on:click="calculate()" class="number btn">=</button>
      </div>
    </div>
    
</template>


<script>
    export default {
        data(){
          return {
          result: '',
          numbers: [1,2,3,4,5,6,7,8,9,0],
          operations: ['+','-','*','/'],
          }           
        },
        methods: {
          input(num) {
            this.result += num;
          },

          calculate() {
            this.result = eval(this.result);
          },
          reset() {
                this.result = '';
                  
          }
        }
    }

 
</script>

 <style scoped>
  .container {
    width: 200px;
    margin: 50px auto;
    background-color: #C2D8B9;
  }

  .input-num {
    margin:0 auto;
    padding: 10px;
    text-align: right;
    color: #5D707F;
    background-color: #E4F0D0;
    font-weight: bold;
    
  }

  .table {
    text-align: center;
  }

  .grid {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
  }




</style>


