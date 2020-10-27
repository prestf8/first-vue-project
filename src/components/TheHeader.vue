<template>
	<div class="header">
		<h4 class="header__title">Markdown Notes</h4>
		<button @click="addTodo" class="header__addTodo"><p>+</p></button>
	</div>
</template>

<script>
	export default {
  name: "TheHeader",

  props: {
    notes: Object
  },

  methods: {
    addTodo() {
      this.$emit("custom-element", Math.random());
    }
  }
};
</script>

<style scoped>
	.header {
		display: flex;
		justify-content: space-between;
		align-items: center;
		padding: 1rem;
	}

	.header__title {
		color: #525151;
	}

	.header__addTodo {
		margin: 0;
		padding: 0;
		font-weight: bold;
		border: none;
		border-radius: 50%;
		box-shadow: 1px 1px 3px 1px #fffccc;
		color: #525151;
		width: 32px;
		height: 32px;
		background-color: #ffef8f;
		text-align: center;
		outline: none;
	}

	.header__addTodo>p {
		margin: 0;
		padding: 0;
		font-size: 1.7rem;
		border-radius: inherit;
		outline: none;
	}

	.header__addTodo:hover {
		cursor: pointer;
		background-color: #fff6bd;
	}
</style>