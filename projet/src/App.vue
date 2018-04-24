<template>
  <div id="app">
    <ul v-for="user in users">
        <li v-for="(item, key) in user">
          <span v-if="key != 'address' && key != 'company'">
            {{ key }} : {{ item }}
          </span>
          <span v-else>{{ key }}</span>
          <ul v-if="key == 'address'">
            <li v-for="(item, key) in user.address">
              <span v-if="key != 'geo'">
                {{ key }} : {{ item }}
              </span>
              <span v-else>
                {{ key }} :
              </span>
              <ul v-if="key == 'geo'">
                <li v-for="(geo, key) in user.address.geo">
                  {{ key }} : {{ geo }}
                </li>
              </ul>
            </li>
          </ul>
          <ul v-if="key == 'company'">
            <li v-for="(item, key) in user.company">{{ key }} : {{ item }}</li>
          </ul>
        </li>
      <!--
      FAÇON PLUS OPTIMISÉE D'APPELER LES DONNÉES DE L'OBJET

        <li v-for="(item, key, index) in user">
        <span v-if="key == 'address' || key == 'geo' || key == 'company'">
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


    <component2></component2>
  </div>

</template>

<script>
import Component2 from './components/Component2'

export default {
  name: 'App',
  components: {
    Component2
  },
  data() {
    return {
      users : {}
    }
  },

  created(){
    let vm = this
    this.$http
      .get('https://jsonplaceholder.typicode.com/users')
      .then(function(response){
        vm.users = response.data
      })
  }
}
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
