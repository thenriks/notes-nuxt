<template>
	<div>
    <textarea></textarea>
    <br>
    <button v-on:click="sendText()">Send</button>
  </div>
</template>

<script>
  export default {
    props: ['token'],
    data() {
      return {
        site: []
      }
    },
    methods: {
      sendText: async function() {
        console.log("token: " + this.$props.token)
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