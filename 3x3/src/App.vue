<template>
  <DigitalClock />
  <LoginForm />
  <QuizTest />
  <PersonTable :information="information" @delete="deleteEntry"/>
  <AddPerson @add="addPersonTable" />
  <OrderList />
  <GameList />
  <Mystery8Ball />
</template>

<script>
import DigitalClock from './components/digitalClock.vue'
import LoginForm from './components/loginForm.vue'
import QuizTest from './components/quizTest.vue'
import PersonTable from './components/personTable.vue'
import AddPerson from './components/addPerson.vue'
import OrderList from './components/orderList.vue'
import GameList from './components/gameList.vue'
import Mystery8Ball from './components/eightBall.vue'

export default {
        name: "App",
        components: { 
            DigitalClock,
            LoginForm, 
            QuizTest, 
            PersonTable, 
            AddPerson, 
            OrderList, 
            GameList, 
            Mystery8Ball
        },
        methods: {
            addPersonTable(event) {
                this.information.push(event)
            },
            deleteEntry(event){
                this.information.splice(event, 1);
            },
        },
     data(){
        return{
            information: [
                {
                firstName:'Perminder',
                lastName: 'Dhillon',
                age: 31,
                },
            ],
            person: {
                firstName:'',
                lastName:'',
                age: null
                }
            
          }
      },
}
</script>

<style>
#app {
    transform: translateY(4rem);
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    justify-content: center;
    text-align: center;
}
.grid-component {
    flex: 1 1 30%;
}
.toggle {
    position: fixed;
    top: 0;
    right: 0;
}
button:hover {
    border: 2px solid white;  
    cursor: pointer;
}

@media only screen and (max-width: 1000px) {
    body {
        transform: scale(80%);
        transform: translateY(1rem);
    }
    #app {
        display: inline;
    }
    .grid-component {
        padding: 5rem;
    }
    .time {
        transform: scale(3);
    }
    .items-list {
        display: inline;
    }
}
</style>
