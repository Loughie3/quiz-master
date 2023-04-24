<template>
  <div class="results">
    <h2>Quiz Results</h2>
    <p v-if="resultsAvailable">
      You scored {{ score }} out of {{ totalQuestions }}.
    </p>
    <p v-else>No results available. Please take the quiz first.</p>
    <div v-if="resultsAvailable">
      <ol>
        <li v-for="(question, index) in questions" :key="index">
          {{ question }}<br />
          Your answer: <strong>{{ userAnswers[index] }}</strong>
          <span v-if="userAnswers[index] === correctAnswers[index]"
            >Correct!</span
          >
          <span v-else>
            Incorrect. The correct answer is:
            <strong>{{ correctAnswers[index] }}</strong>
          </span>
        </li>
      </ol>
    </div>
  </div>
</template>

<script>
export default {
  name: "Results",
  props: {
    score: {
      type: Number,
      required: false,
      default: null,
    },
    totalQuestions: {
      type: Number,
      required: true,
    },
    questions: {
      type: Array,
      required: true,
    },
    userAnswers: {
      type: Array,
      required: true,
    },
    correctAnswers: {
      type: Array,
      required: true,
    },
  },
  computed: {
    resultsAvailable() {
      return this.score !== null;
    },
  },
};
</script>

<style scoped>
.results {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: 1rem;
}

ol {
  width: 100%;
  margin-bottom: 1rem;
}
</style>
