<template>
	<div id="app">
		<div class="app__main">
			<TheHeader @custom-element="addNote" :notes="notes"></TheHeader>
			<ul>
				<li class="app__notes" v-for="n in notes" :key="n.id">
					<Note :id="n.id" @delete-note="deleteNote"></Note>
				</li>
			</ul>
		</div>
	</div>
</template>

<script>
	import TheHeader from "./components/TheHeader.vue";
import Note from "./components/Note.vue";

export default {
  name: "App",
  components: {
    TheHeader,
    Note
  },

  data() {
    return {
      notes: [{ id: 0 }]
    };
  },

  methods: {
    addNote(generated) {
      this.notes.unshift({ id: generated, label: "" });
    },

    deleteNote(noteId) {
      console.log(noteId);
      let index = this.notes.findIndex(element => element.id == noteId);
      this.notes.splice(index, 1);
    }
  }
};
</script>

<style>
	* {
		margin: 0;
		padding: 0;
		box-sizing: border-box;
	}

	#app {
		font-family: Avenir, Helvetica, Arial, sans-serif;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
		background-color: #ffe54f;
		min-height: 100vh;
		height: auto;
	}

	.app__main {
		width: 95%;
		height: 100%;
		max-width: 500px;
		margin: 0 auto;
		color: #2c3e50;
		text-align: center;
	}

	.app__notes {
		list-style: none;
		margin-bottom: 1rem;
	}
</style>