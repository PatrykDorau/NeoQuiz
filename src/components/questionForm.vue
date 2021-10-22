<template>
  <div class="container">
    <img src="lakier1.png" alt="1" width="300px" height="300px">
    <h1>{{currentQuestion.value}}</h1>
      <div class="list">
        <ul>
          <li @click="handleClick(index)" :key="index" v-for="(answer, index) in currentQuestion.answers">
            {{ answer.value }}
          </li>
        </ul>
      </div>
  </div>
</template>

<script>
export default {
  name: 'questionForm',
  props: {
    currentQuestion: Object,
    questionsArray: Array
  },
  data () {
    return{
      nextQuestionKey: 0
    }
  },
  methods: {
    handleClick(index) {
      //Zapisać key wybranej odpowiedzi i wybrac nowe pytanie
      console.log('click', index)
      let selectedAnswer = this.currentQuestion.answers[index]
      let nextQuestionKey = selectedAnswer.key
      this.$emit('filterArray', nextQuestionKey)
      // let filteredArray = []
      // for(let i = 0; i< this.questionsArray.length; i++){
      //   if(this.questionsArray[i].key === nextQuestionKey){
      //     filteredArray.push(this.questionsArray[i])
      //   }
      // }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
h1 {
  box-shadow:1px 1px 5px 1px #f3f3f3;
  width:50vw;
  height: 50vh;
  border:1px solid black;
  border-radius: 5px;
  text-align: center;
  padding-top: 5px;
  margin: auto;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  margin: 10px 10px;
  box-shadow:1px 1px 5px 1px #f3f3f3;
   border:1px solid black;
  border-radius: 5px;
  width: 100%;
  height:50px;
  padding-top: 25px;
  cursor: pointer;
  font-weight: bold;
}
a {
  color: #42b983;
}

.container {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  height: 40vh;
}

.list {
  width: 40vw;
  height:100vh;
}
li:hover {
  background-color: rgb(140, 181, 153);
   transform:scale(1.1);
   transition: 0.5s ease-in-out;
}
</style>
