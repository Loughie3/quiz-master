<template>
  <div class="quiz">
    <h2>Generated Quiz</h2>
    <ol>
      <li v-for="(question, index) in questions" :key="index">
        {{ question }}
        <input
          v-model="userAnswers[index]"
          type="text"
          :placeholder="'Answer ' + (index + 1)"
        />
      </li>
    </ol>
    <button @click="submitQuiz">Submit</button>
  </div>
</template>

<script>
export default {
  name: "Quiz",
  props: {
    questions: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      userAnswers: [],
    };
  },
  created() {
    this.userAnswers = new Array(this.questions.length).fill("");
  },
  methods: {
    submitQuiz() {
      this.$emit("quiz-submitted", this.userAnswers);
    },
  },
};
</script>

<style scoped>
.quiz {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: 1rem;
}

ol {
  width: 100%;
  margin-bottom: 1rem;
}

button {
  margin-top: 1rem;
}
</style>
