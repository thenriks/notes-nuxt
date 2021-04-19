<template>
	<div class="element">
		<div>
			<a :href="url" target="_blank">{{ url }}</a>
		</div>
		<div>
			<button v-if="edit == true" v-on:click="removeElement()">X</button>
		</div>
	</div>
</template>

<script>
  export default {
    props: ['url', 'eid', 'edit'],
    methods: {
    	removeElement: async function() {
    		this.$parent.removeElement(this.$props.eid)
    	}
    }
  }
</script>

<style>
.element {
	display: flex;
}
</style>