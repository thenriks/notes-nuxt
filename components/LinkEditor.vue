<template>
	<div>
    <input type="text" v-model="newLink">
    <button v-on:click="sendLink()">Send</button>
  </div>
</template>

<script>
  export default {
    props: ['token'],
    data() {
      return {
        newLink: "",
        site: []
      }
    },
    methods: {
      sendLink: async function() {
        const r = await this.$http.$post('http://127.0.0.1:8000/add_link', {token: this.$props.token, url: this.newLink})
        this.$parent.refreshSite()
      }
    }
  }
</script>

<style>
.site-element {
  background-color: #ccc;
  border-bottom: 2px solid white;
    font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}
</style>