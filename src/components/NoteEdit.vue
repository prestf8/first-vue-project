<template>
	<div class="note-edit">
		<div class="note__controls">
			<p class="note__status">Editing...</p>
			<p class="note__delete" @click="deleteNote">Delete</p>
		</div>
		<textarea class="note-edit__text" @blur="unFocusEvent" v-model="newLabel">
      {{ label }}
    </textarea>
	</div>
</template>

<script>
	export default {
  name: "NoteEdit",

  props: {
    label: String,
    id: Number
  },

  data() {
    return {
      newLabel: this.label,
    }
  },

  methods: {
    deleteNote() {
      this.$emit("delete-note", this.id);
    },

    unFocusEvent() {
      // console.log(this.newLabel);
      this.$emit("un-focus", this.newLabel);
    }
  }
};
</script>

<style scoped>
	.note-edit {
		width: 95%;
		margin: 0 auto;
		border-radius: 3px;
		text-align: left;
	}

	.note__controls {
		color: red;
		text-align: right;
		background-color: #fff9d6;
		display: flex;
		justify-content: space-between;

		font-size: 0.8rem;
	}

	.note__delete:hover {
		cursor: pointer;
		color: darkred;
	}

	.note-edit__text {
		display: block;
		max-width: 495px;
		width: 100%;
		height: 160px;
		padding: 0.6rem;
		overflow-x: scroll;

		background-color: #fffdf2;
	}
</style>