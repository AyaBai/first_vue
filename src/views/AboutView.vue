<template>
  <!-- <div class="container">
      <div class="input-num">
        {{calculatorValue || 0}}
       </div>


    </div> -->

  <div class="about">
    <!-- <h1>This is an about page</h1> -->
    <button @click="increment">{{ count }}</button>
  </div>
  <div>
      <div class="container">
        <div id="container">
          <button class="q-text" v-on:click="show = !show">How do I return something to you from Europe?</button>
          <div class="a-text" v-show="show">
            <p >Returning something from Belgium, Czech Republic or Portugal? You’ll no longer receive a paper returns slip with your order. Instead, you'll need to create a return through your Account. </p>
          </div>
        </div>
        <div id="cont-2">
          <button class="q-text" v-on:click="show2= !show2">Where is my order?</button>
          <div class="a-text">
            <p  v-show="show2">Track your order,Check the estimated delivery date </p>
          </div>
        </div>
        <div>
          <button class="q-text" v-on:click="show3= !show3">What is your returns policy?</button>
          <div class="a-text" v-show="show3">
            <p>We get it, sometimes something just doesn't work for you and you want your money back. Don't worry, as long as an item is still in its original condition, we accept returns, subject to the rules below, which includes rules around fair use. None of these rules affect your statutory rights.</p>
          </div>
        </div>

      </div>
    </div>


  
</template>

<style>
   .container {
    max-width: 400px;
    margin: 50px auto;
    background-color: #C2D8B9;
  }

  .input-num {
    margin:0 auto;
    padding: 10px;
    text-align: right;
    color: #fff;
    background-color: #E4F0D0;
    font-weight: bold;
    
  }

@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
  .container {
    margin: 0 auto;
    width: 800px;
  }

  .q-text {
    width: 100%;
    background-color: #34D1BF;
  }


</style>

<script>
  export default {
    data() {
      return {
        count:0,
        list: ['asd', 'asd', false],
        show:false,
        show2:false,
        show3:false
        // calculatorValue:'12',
        // calculatorElements:['C','*','','-',7,8,9,'+',4,5,6,'=',0,'.',]
      }
    },
    methods: {
      increment () {
        this.count++
      }
    },
    mounted() {
      // this.increment()
      console.log(this.list)
    }
   
}
</script>