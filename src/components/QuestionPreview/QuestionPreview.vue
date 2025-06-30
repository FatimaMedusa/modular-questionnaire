<template>
  <div class="question-preview">
    <p><strong></strong> {{ question.text }}</p>

    <div v-if="question.type === 'multipleChoice'">
      <p><strong>Antwortoptionen:</strong></p>
      <ul>
        <li
          v-for="(option, index) in question.options"
          :key="index"
          class="radio-item"
        >
          <input
            maxlength="40"
            type="radio"
            :name="'preview-' + question.text"
            :value="option"
          />
          <span>{{ option }}</span>
        </li>
      </ul>
    </div>

    <div v-else-if="question.type === 'openReply'">
      <!-- maxlength auf 40 -->
      <input
        type="text"
        maxlength="40"
        placeholder="Antwort hier eingeben..."
      />
    </div>

    <div v-else-if="question.type === 'yesNo'" class="radio-item">
      <ul>
        <li class="radio-item">
          <label>
            <input type="radio" :name="'yesno-' + question.text" value="ja" />
            Ja
          </label>
        </li>

        <li class="radio-item">
          <label>
            <input type="radio" :name="'yesno-' + question.text" value="nein" />
            Nein
          </label>
        </li>
      </ul>
    </div>

    <div v-else>
      <p>Unbekannter Fragetyp.</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "QuestionPreview",
  props: {
    question: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style scoped lang="scss">
@use "./QuestionPreview.scss" as *;
</style>
