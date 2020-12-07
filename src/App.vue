<template>
  <div id="app">
  <header>
    <div class="container">
      <h1 style="float:left; font-family:verdana; color:white; font-size:40px;font-weight:bold; padding-top:10px;">SmartScore</h1>
      <nav>
          <b-navbar style="background-color:#188642;">
        <template slot="start">
            <b-navbar-item href="#" style="color:white;">
                Home
            </b-navbar-item>
            <b-navbar-item href="#" style="color:white;">
                History
            </b-navbar-item>
            <b-navbar-dropdown label="Info" style="background-color:#188642; color:white;">
                    <b-navbar-item href="#">
                        About
                    </b-navbar-item>
                    <b-navbar-item href="#">
                        Contact
                    </b-navbar-item>
            </b-navbar-dropdown>
        </template>

        <template slot="end">
            <b-navbar-item tag="div">
                <div class="buttons" style="background-color: white;">
                    <a class="button is-light">
                        <strong>Sign up</strong>
                    </a>
                    <a class="button is-light">
                        Log in
                    </a>
                </div>
            </b-navbar-item>
        </template>
    </b-navbar>
    </nav>
    </div>
    </header>

    <div class="clear"></div>
    <div class="container">
      <div class="game">
       <div class="rez" style="height:20%;">
        <img src='./assets/england.jpg' style="width:60px; height:50px; float:left; padding-top:20px;">
        <p style="font-family:verdana; color:black; font-size:40px; font-weight:bold; padding-bottom:30px; padding-top:10px;">English Premier League</p>
          <div v-for="(item,index) in data" v-bind:key="item.id" class="tabl">
            <div class="tekma" style="width:50%; float:left;">   
             <table>
              <td>{{data[index].strHomeTeam}}</td>
              <td>{{data[index].intHomeScore}}:{{data[index].intAwayScore}}</td>
              <td>{{data[index].strAwayTeam}}</td>
             </table>
            </div>              
          </div>
         </div>
        <div class="clear"></div>
        <div class="empty" style="height:100px; width:100%;"></div>
        <div class="mod">
          <h1 style="text-align:center; font-family:verdana; color:black; font-size:40px; padding:0px; font-weight:bold;">MATCH OF A DAY</h1>
          <h2 style="text-align:center; font-family:verdana; color:black; font-size:30px; padding:0px; font-weight:bold;">ATLETICO MADRID VS SEVILLA</h2>
          <h3 style="text-align:center; font-family:verdana; color:black; font-size:50px; padding:0px; font-weight:bold;">15:00</h3>
        </div>
        <div class="mvp">
          <h1 style="text-align:center; font-family:verdana; color:black; font-size:40px; padding-top:5px; font-weight:bold;">PLAYER OF THE MONTH:</h1>
          <h2 style="text-align:center; font-family:verdana; color:black; font-size:50px; padding:30px;">Cristiano Ronaldo</h2>
        </div>
        <div class="clear"></div>
        <div class="foto1" style="width: 50%; height:40%; float:left;">
          <img :src="this.data[1].strThumb" style="width:700px; height:400px; padding:50px;">
        </div>
        <div class="foto2" style="width: 50%; height:40%; float:left;">
          <img src='./assets/kiki.jpg' style="width:700px; height:400px; padding:50px;">
        </div>
      </div>  
    </div>
    <footer>
    </footer>
  </div>
</template>

<script>
  export default {
  name: 'app',
  data () {
    return {
      data:[],
      deta:["asd","bsd","csd","esd"],
    }
  },
  methods: {
  },
  mounted(){
    
    //fetch('https://www.thesportsdb.com/api/v1/json/1/eventsnextleague.php?id=4328')
    fetch('https://www.thesportsdb.com/api/v1/json/1/eventspastleague.php?id=4328')
  .then(response => response.json())
  .then(data =>(this.data = data.events));
  //.then(data =>console.log(data.events));
  //.then(data =>console.log(data));
  }
}
</script>

<style>
*{
  margin:0 auto;
  padding:0;
}
.clear{
  clear: both;
}
.container{
  width: 1500px;
}
header{
  background-color:#188642;
  height:100px;
  color:white;
}
nav{
  float:right;
  padding-top: 10px;
}
rez{
  width: 500px;
  height: 500px;
}
.game{
  width:1500px;
  height:1100px;
  background-color: rgb(222, 235, 222, 0.5);
}
.game b-table{
  float:left;
  padding:20px;
}
.mod{
  height: 25%;
  float: left;
  width: 50%;
  background-color: rgba(2, 250, 2, 0.2);
  padding-top: 50px;
}
.mvp{
  height: 25%;
  float: left;
  background-color: rgba(2, 250, 2, 0.2);
  width: 50%
}
footer{
  background-color:#188642;
  height:100px;
  color:white;
}
#app {
  background-size: cover;
  background-position: top;
  background-image: url('./assets/back_pic.jpg');
}
table {
  font-family: verdana;
  border-collapse: collapse;
  width: 100%;
  text-align: center;
  padding-top: 20px;
  padding-top: 20px;
}
td{
  border: 1px solid #dddddd;
  text-align: center;
  width: 33%;
  padding: 8px;
}
tr:nth-child(even) {
  background-color:  rgba(2, 250, 2, 0.2);
}
</style>
