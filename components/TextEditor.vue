<template>
	<div>
    <textarea v-model="newText"></textarea>
    <br>
    <button v-on:click="sendText()">Send</button>
  </div>
</template>

<script>
  export default {
    props: ['token'],
    data() {
      return {
        newText: "",
        site: []
      }
    },
    methods: {
      sendText: async function() {
        // console.log("token: " + this.$props.token)
        // console.log("text: " + this.newText)
        const r = await this.$http.$post('http://127.0.0.1:8000/add_text', {token: this.$props.token, text: this.newText})
        //console.log(r)
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