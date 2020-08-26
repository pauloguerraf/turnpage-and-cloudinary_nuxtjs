<template>
  <div class="flex justify-center items-center h-screen overflow-hidden">
    <TurnPage class="w-1/2" :options="options">
      <div v-for="resource in resources" v-bind:key="resource.public_id">
        <img
          id="turnp"
          class="imagen"
          :src="
            'https://res.cloudinary.com/nidointeractive/image/upload/v1596560910' +
            '/' +
            resource.public_id +
            '.' +
            resource.format
          "
          draggable="false"
          alt=""
        />
      </div>
    </TurnPage>
  </div>
</template>
<script>
import axios from '~/plugins/axios'
import $ from 'jquery'

export default {
  data() {
    return {
      options: {},
    }
  },
  async asyncData() {
    const { data } = await axios.get(
      //'https://jsonplaceholder.typicode.com/posts'
      'https://res.cloudinary.com/nidointeractive/image/list/v1596595869/comic1.json'
    )
    return { resources: data.resources }
  },
  mounted() {
    this.options = {
      display: 'double',
      acceleration: true,
      autoCenter: true,
      height: document.getElementById('turnp').clientHeight,
      page: 1,
    }
  },
}
</script>
<style></style>
