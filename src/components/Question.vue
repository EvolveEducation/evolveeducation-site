<template>
  <div class="card">
    <div class="card-body">{{question.text}}</div>
    <div class="input-group" v-for="answer in question.possibleAnswers" :key="answer">
      <div class="input-group-prepend">
        <div class="input-group-text">
          <input type="radio" aria-label="Radio button for following text input" />
        </div>
      </div>
      <input type="text" class="form-control" aria-label="Text input with radio button" v-bind="answer"/>
    </div>
  </div>
</template>

<script>
export default {
  name: "Question",
  props: {
    question: Object
  },
  methods: {
    editAnswer: function(e) {e.preventDefault();}
  }
};
</script>