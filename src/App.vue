<template>
  <div id="app">
    <div class="header">
      <meta name="viewport" content="width=device-width, initial-scale=1.0" />
      <img src=".\assets\logo_carb.png" alt="" />
      <h1>Asados carbón de leña</h1>

      <nav>
        <!-- v-if verifica la condición -->
        <button v-on:click="init" v-if="is_auth">Inicio</button>
        <button v-on:click="getBalance" v-if="is_auth">Cliente</button>
        <button v-if="is_auth">Inventario</button>
        <button v-if="is_auth">Ventas</button>
        <button v-if="is_auth">Cerrar Sesión</button>
      </nav>
    </div>

    <div class="main-component">
      <router-view> </router-view>
    </div>

    <div class="footer">
      <p>
        Calle 48 # 27-01. Barrancabermeja, Colombia<br />
        Teléfonos: +57 323 590 9805 - 6220238 - 6021901<br />
        E-mail: carbonlena@hotmail.com
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",

  components: {},

  data: function () {
    return {
      is_auth: localStorage.getItem("isAuth") || false,
    };
  },

  methods: {
init: function(){
if(this.$route.name != "user"){
let username = localStorage.getItem("current_username")
this.$router.push({name: "user", params:{username:username}})
}
},
getBalance: function(){
if(this.$route.name != "user_balance"){
let username = localStorage.getItem("current_username")
this.$router.push({ name:"user_balance",
params:{username:username}
})
}
},
},

  beforeCreate: function(){
localStorage.setItem('current_username', 'camilo24')
localStorage.setItem('isAuth', true)
this.$router.push({name:"user",params:{username:'camilo24'}})
}
</script>

<style>
html {
  box-sizing: border-box;
  height: 100%;
}

*,
*:before,
*:after {
  box-sizing: inherit;
}
body {
  margin: 0 0 0 0;
  background-color: #242424;
  background-image: url("./assets/carnep.jpg");
  background-size: 100%;
  overflow: hidden;
}
.header {
  margin: 0%;
  padding: 0;
  width: 100%;
  height: 10vh;
  min-height: 100px;
  background-color: #242424;
  color: #f5a018;
  display: flex;
  justify-content: space-between;
  align-items: center;
  vertical-align: middle;
  border-bottom: 1px solid #f5a018;
}
.header img {
  width: 90px;
  height: 75px;
  padding: 0%;
  margin: 5%;
}
.header h1 {
  width: 30%;
  text-align: left;
  font-size: 2vw;
}
.header nav {
  height: 100%;
  width: 45%;
  display: flex;
  justify-content: space-evenly;
  align-items: center;
  padding: 10px;
}
.header nav button {
  color: #242424;
  background: #f5a018;
  border: 1px solid #e5e7e9;
  border-radius: 2px;
  padding: 10px, 20px;
  cursor: pointer;
}
.header nav button:hover {
  color: #283747;
  background: #e5e7e9;
  border: 1px solid #e5e7e9;
}
.main-component {
  height: 50%;
  margin: 10% 35% 10% 35%;
  text-align: center;
  background: transparent;
  color: #f5a018;
}
.main-component form {
  height: 50%;

  padding: 50px;
  text-align: center;
  background: #242424;
  border: 1px solid #e5e7e9;
  position: relative;
}

.footer {
  margin: 0;
  padding: 1%;
  width: 100%;
  height: 100%;
  min-height: 100px;
  background-color: #06080c;
  color: #f5a018;
  border-top: 1px solid #f5a018;
  position: fixed;
  display: flex;
  overflow: auto;
}
.footer h2 {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
}
.footer p {
  width: 100%;
  height: 100%;
  justify-content: center;
  justify-items: center;
  vertical-align: middle;
  text-align: center;
}
</style>
