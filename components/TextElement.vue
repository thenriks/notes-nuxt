<template>
	<div class="element">
		<div>
			{{ text }}
		</div>
		<div>
			<button>X</button>
		</div>
	</div>
</template>

<script>
  export default {
    props: ['text']
  }
</script>

<style>
.element {
	display: flex;
}
</style>