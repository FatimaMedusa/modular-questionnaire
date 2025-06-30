<template>
  <div class="question-editor">
    <h2>Neue Frage erfassen</h2>

    <label for="type">Fragetyp:</label>
    <select v-model="question.type" id="type">
      <option disabled value="">Wählen Sie einen Fragetyp aus</option>
      <option value="multipleChoice">Multiple Choice</option>
      <option value="openReply">Freitext</option>
      <option value="yesNo">Ja/Nein</option>
    </select>

    <div v-if="question.type" class="question-section">
      <label for="question">Fragetext:</label>
      <input
        type="text"
        maxlength="40"
        id="question"
        v-model="question.text"
        placeholder="Frage erfassen"
      />

      <!-- Multiple Choice Optionen -->
      <div v-if="question.type === 'multipleChoice'">
        <label>Antwortoptionen:</label>
        <div
          class="card"
          v-for="(option, index) in question.options"
          :key="index"
        >
          <input
            maxlength="40"
            v-model="question.options[index]"
            placeholder="Antwortoption"
          />
          <button class="delete-button" @click="removeOption(index)">
            <i class="fas fa-trash-alt"></i>
          </button>
        </div>
        <button class="add-button" @click="addOption">Option hinzufügen</button>
      </div>

      <!-- Vorschau -->
      <h3>Vorschau:</h3>
      <div class="card">
        <QuestionPreview :question="question" />
      </div>

      <!-- Speichern -->
      <button class="save-button" @click="saveQuestion">Speichern</button>
    </div>
  </div>
</template>

<script>
import QuestionPreview from "../QuestionPreview/QuestionPreview.vue";

export default {
  components: { QuestionPreview },
  data() {
    return {
      question: {
        type: "",
        text: "",
        options: [],
      },
    };
  },
  methods: {
    addOption() {
      this.question.options.push("");
    },
    removeOption(index) {
      this.question.options.splice(index, 1);
    },
    saveQuestion() {
      const existing = JSON.parse(localStorage.getItem("questions") || "[]");
      existing.push(this.question);
      localStorage.setItem("questions", JSON.stringify(existing));
      alert("Frage gespeichert!");
      this.resetForm();
    },
    resetForm() {
      this.question = { type: "", text: "", options: [] };
    },
  },
};
</script>

<style lang="scss">
@use "./QuestionEditor.scss" as *;
</style>
