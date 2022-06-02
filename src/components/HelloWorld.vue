<template>
  <div class="hello">
    <h1>{{ msg }}</h1>

  </div>
</template>

<script>
//need to use 'npm install --sac jexcel' to add configuration
import jexcel from 'jexcel'
import 'jexcel/dist/jexcel.css'

//the raw data that goes into the chrt
var data = [
  ['Accord', 'Honda', '2019-02-12', '', true, '$2,000.00', '#777700'],
  ['Civic', 'Honda', '2018-07-01', '', true, '$4,000.01', '#00777'],
  ['CX-5', 'Mazda', '2013-09-01', '', true, '$7,500,00', '#000777']
]

var options = {
  data: data,
  allowToolBar: true,
  columns: [
    { type: 'text', title: 'Car', width: '120px'},
    { type: 'dropdown', title: 'Make', width: '250px', source: [ 'Honda', 'Mazda', 'Audi' ] },
    { type: 'calendar', title: 'Available', width: '250px' },
    { type: 'image', title: 'Photo', width: '120px' },
    { type: 'checkbox', title: 'Stock', width: '80px' },
    { type: 'numeric', title: 'Price', width: '100px', mask: '$ #.##,00', decimal: ',' },
    { type: 'color', width: '100px', render: 'square' }
  ]
}

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  mounted: function() {
    //function to call jexcel and make chart render to the screen
    let spreadsheet = jexcel(this.$el, options)
    Object.assign(this, {spreadsheet})
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
