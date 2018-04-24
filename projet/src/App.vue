<template>
  <div id="app">
    <ul>
      <li v-for="(item, key, index) in user">
        <span v-if="key != 'address' && key != 'geo' && key != 'company'">
          {{ index }} : {{ key }} : {{ item }}
        </span>
        <span v-else>{{ index }} : {{ key }}</span>
        <ul v-if="key == 'address'">
          <li v-for="(item, key) in user.address">{{ key }} : {{ item }}</li>
        </ul>
        <ul v-if="key == 'geo'">
          <li v-for="(item, key) in user.geo">{{ key }} : {{ item }}</li>
        </ul>
        <ul v-if="key == 'company'">
          <li v-for="(item, key) in user.company">{{ key }} : {{ item }}</li>
        </ul>
      </li>
      <!--
        <li v-for="(item, key, index) in user">
        <span v-if="key == 'address' || key == 'geo' || key == 'company'">    FAÇON PLUS OPTIMISÉE DE D'APPELER LES DONNÉES DE L'OBJET
          {{ index }} : {{ key }}
        </span>
        <span v-else>
          {{ index }} : {{ key }} : {{ item }}
        </span>
        <ul v-if="key == 'address' || key == 'geo' || key == 'company'">
          <li v-for="(subitem, key) in item">{{ key }} : {{ subitem }}</li>
        </ul>
      </li>
      -->
    </ul>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'
import Component2 from './components/Component2'

export default {
  name: 'App',
  components: {
    HelloWorld,
    Component2
  },
  data() {
    return {
      user : {
        id: 1,
        name: "Leanne Graham",
        username: "Bret",
        email: "Sincere@april.biz",
        phone: "1-770-736-8031 x56442",
        website: "hildegard.org",
        address: {
          street: "Kulas Light",
          suite: "Apt. 556",
          city: "Gwenborough",
          zipcode: "92998-3874",
        },
        geo: {
          lat: "-37.3159",
          lng: "81.1496"
        },
        company: {
          name: "Romaguera-Crona",
          catchPhrase: "Multi-layered client-server neural-net",
          bs: "harness real-time e-markets"
        }
      }
    }
  }
}

/*let test = new Vue({
  el : '#app',
  data : {
    message : 'Salut les mecs'
  }
})*/

</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
