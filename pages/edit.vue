<template>
	<div class="container">
  		<div v-if="siteSet">
        <h3 class="subtitle">Edit</h3>

        <div>
          Token: {{ token }}
          <br>
          Address: /sites/{{ siteId }} 
        </div>

        <button v-on:click="editorMode = 1">Text</button>
        <button v-on:click="editorMode = 2">Link</button>
        <TextEditor v-if="editorMode === 1" :token="token" />
        <LinkEditor v-else-if="editorMode === 2" :token="token" />
	  		<Site :site-id="siteId" />
  		</div>
      <div v-else>
        Edit site with token:
        <br>
        <input type="text" name="tokenInput" v-model="token">
        <button v-on:click="sendToken()">Edit</button>
        <hr>
        <button v-on:click="newSite()">Create new</button>
      </div>
  	</div>
</template>

<script>
  export default {
    data() {
      return {
        siteId: 2,
        token: "kCsQBY",
        editorMode: 1,
        siteSet: false,
        fetched: ""
      }
    },
    methods: {
      sendToken: async function() {
        //this.siteId = this.fetchSiteId()
        this.siteId = await this.$http.$get('http://127.0.0.1:8000/site_id/' + this.token)
        this.siteSet = true
      },
      newSite: async function() {
        const siteInfo = await this.$http.$post('http://127.0.0.1:8000/new')
        this.token = siteInfo.token
        this.siteId = siteInfo.sid
        this,siteSet = true
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