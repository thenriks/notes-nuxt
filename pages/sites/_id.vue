<template>
	<div class="container">
  		<div>
	  		<h1>{{site.title}}</h1>
  			<div v-for="el in site.elements">
          <div v-if="el.type === 'text'">
            {{ el.text }}
          </div>
          <div v-else-if="el.type === 'link'">
            <a :href="el.url" target="_blank">{{ el.url }}</a>
          </div>
  			</div>
  		</div>
  	</div>
</template>


<script>
  export default {
    async asyncData({ params, $http }) {
      const site = await $http.$get(`http://127.0.0.1:8000/site/${params.id}`)
      console.log(site)
      return { site }
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