<template>
  <link
    rel="stylesheet"
    href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css"
  />
  <div>
    <nav>
      <button @click="view = 'editor'">Frage erfassen</button>
      <button @click="view = 'list'">Erstellte Fragen</button>
    </nav>

    <QuestionEditor v-if="view === 'editor'" />
    <QuestionList v-else />
  </div>
</template>

<script>
import QuestionEditor from "./components/QuestionEditor/QuestionEditor.vue";
import QuestionList from "./components/QuestionList/QuestionList.vue";

export default {
  components: {
    QuestionEditor,
    QuestionList,
  },
  data() {
    return {
      view: "editor",
    };
  },
};
</script>

<style lang="scss">
@use "./App.scss" as *;
</style>
