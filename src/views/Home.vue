<template>
  <div class="home container mx-auto my-10 py-10">
    <form action="" class="w-6/12 mx-auto text-left">
      <div class="mb-4">
        <label class="block text-gray-700 text-sm font-bold mb-2" for="amount">
          Amount
        </label>
        <input
          class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
          id="amount" type="number" placeholder="Amount" v-model="amount">
      </div>

       <div class="mb-4">
        <label class="block text-gray-700 text-sm font-bold mb-2" for="gst-percent">
          GST %
        </label>
        <input
          class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
          id="gst-percent" type="number" placeholder="GST %" v-model="gstPercent">
      </div>

      <div class="mb-4">
        <p>Amount: {{ amount }}</p>
        <p>GST: {{ gstCalculate }}</p>
        <p>Total: {{ totalAmount }}</p>
      </div>
      
    </form>
  </div>
</template>

<script>
  export default {
    name: 'Home',
    data:function() {
      return {
        amount: null,
        gstPercent: null,
        gstCalculate: null,
        totalAmount: null
      }
    },
    methods:{
        calculateGst(){
           if(!this.amount){
             this.gstCalculate = null;
             this.totalAmount = null;
           }
           if(this.amount && this.gstPercent){
              this.gstCalculate = (parseFloat(this.gstPercent) * parseFloat(this.amount)) / 100;
              this.totalAmount = parseFloat(this.amount) + parseFloat(this.gstCalculate);
           }
        }
    },
    watch:{
      amount(){
         this.calculateGst();
      },
      gstPercent(){
         this.calculateGst();
      }
    }
  }
</script>