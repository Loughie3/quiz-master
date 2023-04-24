<template>
  <form @submit.prevent="submitSelection">
    <div class="study-notes">
      <h2>Paste Your Study Notes</h2>
      <textarea v-model="notes" rows="10" cols="50" required></textarea>
      <br />
    </div>
    <div class="question-selection">
      <h2>Question Selection</h2>
      <label for="question-count"
        >How many Questions would you like to generate?</label
      >
      <select id="question-count" v-model="questionCount" required>
        <option v-for="n in 20" :key="n" :value="n">{{ n }}</option>
      </select>

      <label for="question-type">Question Type:</label>
      <select id="question-type" v-model="questionType" required>
        <option value="true_false">True or False</option>
        <option value="short_answer">Short Answer</option>
        <option value="multiple_choice">Multiple Choice</option>
        <option value="mixed">Mixed</option>
      </select>

      <button type="submit">Submit</button>
    </div>
  </form>
</template>

<script>
export default {
  name: "StudyNotes",
  data() {
    return {
      notes: "",
      questionCount: null,
      questionType: null,
      require: true,
    };
  },
  methods: {
    submitSelection() {
      this.$emit("selection-submitted", {
        questionCount: this.questionCount,
        questionType: this.questionType,
      });
    },
  },
};
</script>

<style scoped>
.study-notes {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: 1rem;
}

textarea {
  width: 100%;
  resize: none;
}

.question-selection {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: 1rem;
}

label {
  margin-right: 0.5rem;
}

button {
  margin-top: 1rem;
}
</style>
