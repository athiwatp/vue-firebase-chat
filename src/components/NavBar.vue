<template lang="html">
  <header class="header">
    <h1 class="logo"><a href="#">Vue Chat</a></h1>
    <ul class="main-nav">
      <li v-if="loggedIn"><router-link to="/logout">Logout</router-link></li>
    </ul>
  </header>
</template>

<script>
import { auth,eventHub } from '../db/firebase'
export default {
  data(){
    return{
      loggedIn: false
    }
  },
  created(){
    var self = this
    eventHub.$on('logged', (event) =>{
      self.loggedIn = event.status
    })
  }
}
</script>

<style lang="css" scoped>

  * {
    box-sizing: border-box;
  }
  ul {
    margin: 0;
    padding: 0;
    list-style: none;
  }
  a {
    color: #34495e;
    text-decoration: none;
  }

  .logo {
    margin: 0;
    font-size: 1.45em;
  }

  .main-nav {
    margin-top: 5px;

  }
  .logo a,
  .main-nav a {
    padding: 10px 15px;
    text-transform: uppercase;
    text-align: center;
    display: block;
  }

  .main-nav a {
    color: #34495e;
    font-size: .99em;
  }

  .main-nav a:hover {
    color: #718daa;
  }
  .header {
    padding-top: .5em;
    padding-bottom: .5em;
    border: 1px solid #a2a2a2;
    background-color: #f4f4f4;
    -webkit-box-shadow: 0px 0px 14px 0px rgba(0,0,0,0.75);
    -moz-box-shadow: 0px 0px 14px 0px rgba(0,0,0,0.75);
    box-shadow: 0px 0px 14px 0px rgba(0,0,0,0.75);
    -webkit-border-radius: 5px;
    -moz-border-radius: 5px;
    border-radius: 5px;
  }

  /* =================================
  Media Queries
  ==================================== */

  @media (min-width: 769px) {
    .header,
    .main-nav {
      display: flex;
    }
    .header {
      flex-direction: column;
      align-items: center;
      .header{
        width: 80%;
        margin: 0 auto;
        max-width: 1150px;
      }
    }

  }

  @media (min-width: 1025px) {
    .header {
      flex-direction: row;
      justify-content: space-between;
    }

  }

</style>
