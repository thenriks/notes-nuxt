<template>
	<div>
  		<div>
        <div v-if="$fetchState.pending">Loading....</div>
        <div v-else-if="$fetchState.error">Error while fetching site</div>
        <div v-else>
    			<div v-for="el in site.elements">
            <div v-if="el.type === 'text'" class="site-element">
              <TextElement :text="el.text" :eid="el.id" :edit='edit' />
            </div>
            <div v-else-if="el.type === 'link'" class="site-element">
              <LinkElement :url="el.url" :eid="el.id" :edit='edit' />
            </div>
    			</div>
        </div>
  		</div>
  	</div>
</template>

<script>
  export default {
    props: ['siteId', 'edit', 'token'],
    data() {
      return {
        site: []
      }
    },
    async fetch() {
      this.site = await fetch(
        `https://agile-river-85748.herokuapp.com/site/` + this.siteId
      ).then(res => res.json())
    },
    methods: {
      refreshSite: async function() {
        this.site = await this.$http.$get('https://agile-river-85748.herokuapp.com/site/' + this.siteId)
      },
      removeElement: async function(eid) {
        const r = await this.$http.$post('https://agile-river-85748.herokuapp.com/remove', {token: this.$props.token, id: eid})
        this.refreshSite()
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