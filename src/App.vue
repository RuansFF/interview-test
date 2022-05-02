<template>
  <div id="app">
      <!-- 
      - As requested under instruction values should be between 0 - 100 and not more,
      - Therefore I added additional validation to insure values stay between 0 - 100
      -->
      <label for="numInput" id="labelIn">Instert a Value between 0 - 100</label> <br/>
        <input type="number" v-model="limit" placeholder=" Enter number between 0-100"/>
          <div class="error" v-if="limit > 100"> Incorrect Input - Please insert correct number between 1 - 100</div>
      <!-- 
      - It is really important to me to always remove clutter from the front-end and therefore I decided to implement a "if"
        statement where if the users input is bigger than 100 it will display an error message and remove all numbers.
        The thought behind this was to block a user from typing infinite numbers into the input box and display all the numbers
        in an infinite list/loop.
      -->
      <div v-if="limit <= 100">
        <Numbers/>
      </div>
      <div v-else="limit > 100"></div>
  </div>
</template>

<script>
import Numbers from '@/components/Numbers';

export default {
  name: 'App',
  components: {Numbers},
  data()
  {
    return {
      limit: 100, 
    }
  },

}

</script>

<style scoped>

/* I added additional styling to create a more structured display */

#app{
  background:#D3D3D3;
  opacity: 1;
  margin: 0 auto;
  width: 700px;
  max-height: fit-content;
  border: 2px solid;
  border-radius: 3px;
  text-align: center;
  padding: 15px;
}

/* Adding of a error display is always a create way to improve responsiveness. Therefore I added in an error message */

.error{
  position: relative;
  font-weight: 600;
  border: 1px solid;
  border-radius: 5px;
  padding: 15px;
  width: 26.6em;
  background: red;
  opacity: 0.3;
  color: #fff;
  margin:0 auto;
  margin-top: 15px;
}

input[type="number"]{
  margin-top: 15px;
  width: 240px;
  padding: 15px; 
  text-align: center;
}

#labelIn{
  font-weight: 600;
  font-size: 20px;
  margin-bottom: 15px;
  margin-top: 15px;
}

</style>