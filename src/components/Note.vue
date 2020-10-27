<template>
	<div class="note" v-if="!editing">
		<div class="note__controls">
			<p class="note__status">Double click to Edit</p>
			<p class="note__delete" @click="deleteNote">Delete</p>
		</div>
		<div class="note__text" @click="toEdit">
			{{ label }}
		</div>
	</div>
	<NoteEdit :id="id" :label="label" @un-focus="doneEdit" v-else> </NoteEdit>
</template>

<script>
	import NoteEdit from "./NoteEdit.vue";

export default {
  name: "Note",

  components: {
    NoteEdit
  },

  data() {
    return {
      editing: false,
      label: "",
    };
  },

  props: {
    id: Number
  },

  methods: {
    deleteNote() {
      this.$emit("delete-note", this.id);
    },

    toEdit() {
      
      this.editing = true;
    },

    doneEdit(newLabel) {
      this.label = newLabel;
      this.editing=false;
    },
  }
};
</script>

<style scoped>
	.note {
		width: 95%;
		margin: 0 auto;
		border-radius: 5px;
		text-align: left;
	}

	.note__controls {
		color: red;
		padding: 0.6rem;
		background-color: #fff9d6;
		display: flex;
		justify-content: space-between;

		font-size: 0.8rem;
	}

	.note__delete:hover {
		cursor: pointer;
		color: darkred;
	}

	.note__text {
		max-width: 495px;
		height: 160px;
		padding: 0.6rem;
		overflow-x: scroll;

		background-color: #fffdf2;
	}

	.note__text:hover {
		cursor: text;
	}
</style>