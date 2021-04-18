<template>
	<div>
		<a :href="url" target="_blank">{{ url }}</a>
	</div>
</template>

<script>
  export default {
    props: ['url']
  }
</script>