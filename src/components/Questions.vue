<template>
  <div class="questions-ctr">
    <div class="progress">
      <div
        class="bar"
        v-bind:style="{
          width: `${(questionsAnsweredProps / questionsProps.length) * 100}%`,
        }"
      ></div>
      <div class="status">
        {{ questionsAnsweredProps }} out of
        {{ questionsProps.length }} questions answered
      </div>
    </div>
    <transition-group name="fade"> 
      <div
        class="single-question"
        v-for="(question, qIndex) in questionsProps"
        v-bind:key="question.q"
        v-show="questionsAnsweredProps === qIndex"
      >
        <div class="question">{{ question.q }}</div>
        <div class="answers">
          <div
            class="answer"
            v-for="answer in question.answers"
            v-bind:key="answer.text"
            v-on:click.prevent="selectAnswer(answer.is_correct)"
          >
            {{ answer.text }}
          </div>
        </div>
      </div>
    </transition-group>
  </div>
</template>


<script >
export default {
  name: "QuestionQuiz",
  props: ["questionsProps", "questionsAnsweredProps"],
  data() {},
  emits: ["questionAnsweredEmit"],
  methods: {
    selectAnswer(is_correct) {
      this.$emit("questionAnsweredEmit", is_correct);
    },
  },
};
</script>


<style scoped>
</style>