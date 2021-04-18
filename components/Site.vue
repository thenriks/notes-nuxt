<template>
	<div>
  		<div>
        <div v-if="$fetchState.pending">Loading....</div>
        <div v-else-if="$fetchState.error">Error while fetching site</div>
        <div v-else>
    			<div v-for="el in site.elements">
            <div v-if="el.type === 'text'" class="site-element">
              {{ el.text }}
            </div>
            <div v-else-if="el.type === 'link'" class="site-element">
              <a :href="el.url" target="_blank">{{ el.url }}</a>
            </div>
    			</div>
        </div>
  		</div>
  	</div>
</template>

<script>
  export default {
    props: ['siteId'],
    data() {
      return {
        site: []
      }
    },
    async fetch() {
      this.site = await fetch(
        `http://127.0.0.1:8000/site/` + this.siteId
      ).then(res => res.json())
    },
    methods: {
      refreshSite: async function() {
        this.site = await this.$http.$get('http://127.0.0.1:8000/site/' + this.siteId)
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