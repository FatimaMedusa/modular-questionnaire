<template>
  <div class="question-list">
    <h2>Gespeicherte Fragen</h2>

    <div v-if="questions.length === 0">
      <p>Es sind noch keine Fragen gespeichert.</p>
    </div>

    <ul v-else>
      <li v-for="(q, index) in questions" :key="index" class="card">
        <strong>{{ q.text }}</strong>
        <span>({{ getLabel(q.type) }})</span>
        <button class="delete-button" @click="deleteQuestion(index)">
          <i class="fas fa-trash-alt"></i>
        </button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "QuestionList",
  data() {
    return {
      questions: [],
    };
  },
  mounted() {
    this.loadQuestions();
  },
  methods: {
    loadQuestions() {
      this.questions = JSON.parse(localStorage.getItem("questions") || "[]");
    },
    deleteQuestion(index) {
      if (confirm("Diese Frage wirklich löschen?")) {
        this.questions.splice(index, 1);
        localStorage.setItem("questions", JSON.stringify(this.questions));
      }
    },
    getLabel(type) {
      switch (type) {
        case "multipleChoice":
          return "Multiple Choice";
        case "openReply":
          return "Freitext";
        case "yesNo":
          return "Ja/Nein";
        default:
          return "Unbekannt";
      }
    },
  },
};
</script>

<style lang="scss">
@use "./QuestionList.scss" as *;
</style>
