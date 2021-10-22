<template>
  <div id="app">
     <div class="wrapper">
    <questionForm
    v-if="this.resultsArray.length <= questionsNumber"
     :currentQuestion="filteredArray[index]" 
     :questionsArray="questionsArray" 
     @filterArray="filteredQuestionsArray"
    />
    <resultForm
      v-if="this.resultsArray.length > questionsNumber"
      :productsArray="productsArray"
      :resultsArray="resultsArray"
    />
    </div>
  </div>
</template>

<script>
import questionForm from './components/questionForm.vue'
import resultForm from './components/resultForm.vue'

export default {
  name: 'App',
  methods: {
    filteredQuestionsArray(arg) {
      console.log(arg, 'arg')
      this.key = arg;
      this.filteredArray = this.questionsArray.filter(item => item.key === arg)
      console.log(this.filteredArray,'filterd')
      this.index = Math.floor(Math.random() * this.filteredArray.length - 0.01)
      console.log(this.index, 'index')
      // dodajemy key do tablicy wyniku żeby potem uzyskać produkty
      this.resultsArray.push(arg)
      console.log(this.resultsArray, 'wynik')
      //wyrzucic wybrane pytanie z puli
        // let currentQuestion = this.filteredArray[this.index]
        // let newArr = this.filteredArray.filter(item => item.id !== currentQuestion.id )
        // this.filteredArray = newArr

    }
  },
  components: {
    questionForm,
    resultForm
  },
  data() {
    return{
      index: 0,
      questionsNumber: 5,
      questionsArray: [
        {
          id: 1,
          key:0,
          value: 'mani czy pedi?',
          answers: [
            {
              value:1,
              key:2
            },
            {
              value:2,
              key:1
            },
            {
              value:3,
              key:4
            },
          ]
        },
        {
          id: 2,
          key:1,
          value: 'czemu?',
          answers: [
            {
              value:1,
              key:2
            },
            {
              value:2,
              key:3
            },
            {
              value:3,
              key:5
            },
          ]
        },
        {
          id: 3,
          key:2,
          value: 'Po co?',
          answers: [
            {
              value:1,
              key:3
            },
            {
              value:2,
              key:4
            },
            {
              value:3,
              key:3
            },
          ]
        },
        {
          id: 4,
          key:3,
          value: 'gdzie?',
          answers: [
            {
              value:1,
              key:1
            },
            {
              value:2,
              key:4
            },
            {
              value:3,
              key:4
            },
          ]
        },
        {
          id: 5,
          key:4,
          value: 'kto?',
          answers: [
            {
              value:1,
              key:2
            },
            {
              value:2,
              key:4
            },
            {
              value:3,
              key:5
            },
          ]
        },
        {
          id: 6,
          key:5,
          value: 'jak?',
          answers: [
            {
              value:1,
              key:1
            },
            {
              value:2,
              key:3
            },
            {
              value:3,
              key:2
            },
          ]
        }
      ],
      filteredArray: [
        {
          id: 1,
          key:0,
          value: 'manicure czy pedicure?',
          answers: [
            {
              value:1,
              key:2
            },
            {
              value:2,
              key:1
            },
            {
              value:3,
              key:4
            },
          ]
        }
      ],
      resultsArray: [],
      productsArray: [
        {
          name: 'baza1',
          picture: 111,
          id: 1,
          key: [1,3,4,2]
        },
        {
          name: 'baza2',
          picture: 111,
          id: 2,
          key: [2,3,5]
        },
        {
          name: 'baza3',
          picture: 111,
          id: 3,
          key: [2,3,4]
        },
        {
          name: 'baza4',
          picture: 111,
          id: 4,
          key: [2,3,1]
        }
      ]
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  display: flex;
  justify-content: center;
  align-items: center;
}
.wrapper {
  width: 60vw;
  height: 60vh;
  margin: auto;
  position: absolute;
  top:50%;
  left:50%;
  transform: translate(-50%, -50%);
  display:flex;
  justify-content: center;
  align-items: center;
  border-radius: 5px;
}
</style>
