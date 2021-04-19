<template>
	<div class="element">
		<div>
			{{ text }}
		</div>
		<div>
			<button v-on:click="removeElement()">X</button>
		</div>
	</div>
</template>

<script>
  export default {
    props: ['text', 'eid'],
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