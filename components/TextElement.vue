<template>
	<div class="element">
		<div>
			{{ text }}
		</div>
		<div v-if="">
			<button v-if="edit == true" v-on:click="removeElement()">X</button>
		</div>
	</div>
</template>

<script>
  export default {
    props: ['text', 'eid', 'edit'],
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