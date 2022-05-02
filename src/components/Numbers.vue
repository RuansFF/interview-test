<template>
  <div class="container">
    <!-- I believe the best way for tracking mouse movements would rather be to use vue.js "v-on" functions like shown below -->
    <div class="number" :id="'number-'+number" v-for="number in n()" :key="number" v-on:mouseover="hov(number)" v-on:mouseout="reset">
      {{number}}
    </div>   
  </div>
</template>

<script>
export default {
  data()
  {
    return {
      limit: this.$parent.limit,
      numbers: [],
    }
  },
  watch: {
    ['$parent.limit'](newLimit)
    {
      this.limit = newLimit;
    }
  },
  methods: {
    n()
    {
      let numbers = [];
      for(var i = 0; i < this.limit; i++)
      {
        numbers = [...numbers, i];
      }
      return numbers.sort(() => Math.random() - 0.5);
      
    },
    hov(number)
    {
      const nums = document.querySelectorAll('.number');
      for(let i = 0; i < nums.length; i++)
      {
        const num = nums[i].textContent.trim();
        if(number % num === 0)
        {
          nums[i].classList.add('active')
          console.log('divisor', num)
        }
      }
    },
    reset()
    {
      const nums = document.querySelectorAll('.number');
      nums.forEach(num => num.classList.remove('active')) 
    },
  }
}
</script>

<style scoped>

	.number {
		display: inline-block;
		padding: 5px;
		background-color: lightgrey;
		margin: 5px;
    width: 2em;
    text-align: center;
    border-radius: 2px;
	}

  /* 
  I was thinking of creating a method/function where you just send over the divirsor and display them on the front-end, I rather chose
  to just display the divisors in red and the active number in blue to display the difference better.
  */

  .number:hover{
    background-color:blue;
  }

	.active {
		background-color: red;
    opacity: 0.3;
    color: #FFF;
	}

  /* 
  As most of the logical functioning works perfectly I thought that the main focus should be to implement front-end changes and make the 
  array of numbers easier to read and display. Therefore I create another div/container around all the elements and styled them accordingly.
  */

  .container{
    margin: auto;
    max-width: fit-content;
    max-height: fit-content;
    padding: 10px;
  }
  
</style>
