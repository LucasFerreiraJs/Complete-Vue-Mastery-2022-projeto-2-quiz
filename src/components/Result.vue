<template>
  <div class="result">
    <div class="title">{{ resultsProps[resultIndex].title }}</div>
    <div class="desc">{{ resultsProps[resultIndex].desc }}</div>
  </div>
</template>

<script>
export default {
  name: "ResultQuiz",
  data() {},
  props: ["resultsProps", "totalCorrectProps"],
  computed: {
    resultIndex() {
      let index = 0;

      this.resultsProps.forEach((el, i) => {
        if (
          el.min <= this.totalCorrectProps &&
          el.max >= this.totalCorrectProps
        ) {
          index = i;
        }
      });

      return index;
    },
  },
};
</script>

<style scoped>
</style>