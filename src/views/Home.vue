<template>
  <div>
    <StudyNotes @selection-submitted="onSelectionSubmitted" />

    <Quiz
      :questions="generatedQuestions"
      @quiz-submitted="onQuizSubmitted"
      v-if="quizGenerated"
    />

    <Results
      :score="score"
      :totalQuestions="generatedQuestions.length"
      :questions="generatedQuestions"
      :userAnswers="userAnswers"
      :correctAnswers="correctAnswers"
      v-if="quizSubmitted"
    />
  </div>
</template>

<script>
import StudyNotes from "../components/StudyNotes.vue";
import Quiz from "../components/Quiz.vue";
import Results from "../components/Results.vue";
export default {
  name: "HomeVue",
  components: {
    StudyNotes,
    Quiz,

    Results,
  },
  data() {
    return {
      quizGenerated: false,
      generatedQuestions: [
        { question: "Question 1" },
        {
          question: "Question 2",
        },
        {
          question: "Question 3",
        },
        {
          question: "Question 4",
        },
        {
          question: "Question 5",
        },
        {
          question: "Question 6",
        },
        {
          question: "Question 7",
        },
        {
          question: "Question 8",
        },
        {
          question: "Question 9",
        },
        {
          question: "Question 10",
        },
      ],
      quizSubmitted: false,
      userAnswers: [""],
      score: null,
      correctAnswers: [],
    };
  },
  methods: {
    onSelectionSubmitted({ questionCount, questionType }) {
      this.generateQuestions(questionCount, questionType);
      // Save the submitted notes, question count, and question type
      // Generate the quiz questions using GPT-4, based on the submitted notes and selections
      this.quizGenerated = true;
    },
    generateQuestions(questionCount, questionType) {
      // Generate questions using GPT-4 or any other method
      // Use the submitted notes, question count, and question type

      // For now, we'll use the existing questions in generatedQuestions
      this.generatedQuestions = this.generatedQuestions.slice(0, questionCount);
    },

    onQuizSubmitted(answers) {
      this.userAnswers = answers;
      this.quizSubmitted = true;
      // Evaluate the answers using GPT-4 and display the results
    },

    // ...
  },
};
</script>
<style></style>
