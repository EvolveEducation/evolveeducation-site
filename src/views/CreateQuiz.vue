<template>
  <div>
    <br />
    <h2>Create a Quiz</h2>
    <div v-for="question in questions" :key="question.id" class="card">
      <div class="card-body">
        <h4>Question Text:</h4>
        <div class="input-group mb-3">
          <input
            type="text"
            class="form-control"
            placeholder="Question Text"
            aria-label="Question Text"
            v-model="question.text"
          />
        </div>
      </div>
      <p>Possible Answers:</p>
      <form>
        <div class="input-group" v-for="answer in question.possibleAnswers" :key="answer.id">
          <div class="input-group-prepend">
            <div class="input-group-text">
              <input
                type="radio"
                aria-label="Radio button for correct answer"
                name="correctAnswer"
                v-bind:id="question.id+'-'+answer.id"
                v-on:change="editCorrect"
              />
            </div>
          </div>
          <input
            type="text"
            class="form-control"
            aria-label="Text input with radio button"
            v-model="answer.text"
            v-on:input="editAnswer"
          />
        </div>
      </form>
      <button
        v-on:click="deleteQuestion"
        type="button"
        :id="'question-'+question.id"
        class="btn btn-danger deleteBtn"
      >Delete Question</button>
    </div>
    <button v-on:click="newQuestion" type="button" class="btn btn-primary actionBtn">Create Question</button>
    <button v-on:click="submit" type="button" class="btn btn-success actionBtn">Download Quiz</button>

    <div v-if="error !== null" class="alert alert-danger">
        {{error}}
    </div>
  </div>
</template>

<style scoped>
.card {
  padding: 10px;
  margin: 10px 0px;
}

.deleteBtn {
  margin-top: 10px;
}

.actionBtn {
  margin: 10px 5px;
}
</style>

<script>
export default {
  data: () => ({
    questions: [
      {
        id: 0,
        text: "",
        possibleAnswers: [{ id: 0, text: "" }],
        correctAnswer: null
      }
    ],
    error: null
  }),
  methods: {
    newQuestion: function() {
      this.questions.push({
        id: this.questions.length + 1,
        text: ``,
        correctAnswer: null,
        possibleAnswers: [{ id: 0, text: "" }]
      });
    },
    editAnswer: function() {
      const fullQuestions = this.questions.filter(
        q => q.possibleAnswers.filter(a => a.text === "").length === 0
      );
      fullQuestions.forEach(q => {
        const lastQ = q.possibleAnswers[q.possibleAnswers.length - 1];
        q.possibleAnswers.push({ id: lastQ.id + 1, text: "" });
      });
      const moreThanOneEmpty = this.questions.filter(
        q => q.possibleAnswers.filter(a => a.text === "").length > 1
      );
      moreThanOneEmpty.forEach(q => {
        const newIndex = q.possibleAnswers[q.possibleAnswers.length - 1].id + 1;
        q.possibleAnswers = q.possibleAnswers.filter(a => a.text !== "");
        if (!q.possibleAnswers.find(a => a.id === q.correctAnswer)) {
          q.correctAnswer = null;
        }
        q.possibleAnswers.push({ id: newIndex, text: "" });
      });
    },
    editCorrect: function(e) {
      const parts = e.target.id.split("-");
      const qNum = Number.parseInt(parts[0]);
      const selectedQuestion = this.questions.find(q => q.id === qNum);
      selectedQuestion.correctAnswer = Number.parseInt(parts[1]);
    },
    submit: function() {
      let error = null;
      const questions = [];
      for(var j = 0; j < this.questions.length; j++) {
          const q = this.questions[j];
          console.log(q);
        const answers = [];
        let correctAnswer = -1;
        for (var i = 0; i < q.possibleAnswers.length; i++) {
          const answer = q.possibleAnswers[i];
          if (answer.text.length > 0) {
            answers.push(answer.text);
            if (q.correctAnswer === answer.id) {
              correctAnswer = answers.length - 1;
            }
          }
        }

          if (correctAnswer === -1) {
            error = "You must select a non empty answer as correct!";
            break;
          }
          questions.push( {
            questionText: q.text,
            possibleAnswers: answers,
            correctAnswer
          });
      }
      if(!error) {
        const dataToEncode = JSON.stringify({questions});
        const dataEncoded = btoa(dataToEncode);
        const linkElement = document.createElement('a');
        linkElement.setAttribute('href', 'data:text/plain;charset=utf-8,' + dataEncoded);
        linkElement.setAttribute('download', 'quiz.bactgrowth');
        linkElement.style.display = 'none';
        document.body.appendChild(linkElement);
        linkElement.click();
        document.body.removeChild(linkElement);
      }
      
      this.error = error;
    },
    deleteQuestion: function(e) {
      const qDeleteId = Number.parseInt(e.target.id.replace("question-", ""));
      this.questions = this.questions.filter(q => q.id !== qDeleteId);
    }
  }
};
</script>