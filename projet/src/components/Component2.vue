<template>
  <div class="pic">
    <ul>
      <li v-for="(item, key, index) in pictures">
        <span v-if="key == 'url'">
          {{ key }} : <img :src="pictures.url">
        </span>
        <span v-else-if="key == 'thumbnailUrl'">
          {{ key }} : <img :src="pictures.thumbnailUrl">
        </span>
        <span v-else>
          {{ key }} : {{ item }}
        </span>
      </li>
    </ul>
  </div>
</template>

<script>
  export default {
    name: "component2",
    data() {
      return {
        pictures: {
          albumId: 1,
          id: 1,
          title: "accusamus beatae ad facilis cum similique qui sunt",
          url: "http://placehold.it/600/92c952",
          thumbnailUrl: "http://placehold.it/150/92c952"
        }
      }
    }
  }

</script>

<style>

</style>
