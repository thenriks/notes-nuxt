<template>
	<div class="container">
  		<div>
        <h1 class="subtitle">Edit</h1>
        <button v-on:click="editorMode = 1">Text</button>
        <button v-on:click="editorMode = 2">Link</button>
        <TextEditor v-if="editorMode === 1" token="token" />
        <LinkEditor v-else-if="editorMode === 2" token="token" />
	  		<Site :site-id="siteId" />
  		</div>
  	</div>
</template>

<script>
  export default {
    data() {
      return {
        siteId: 7,
        token: "",
        editorMode: 1
      }
    }
  }
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
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
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

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

.links {
  padding-top: 15px;
}
</style>