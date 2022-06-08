<template>
  <DigitalClock />
  <LoginForm />
  <QuizTest />
  <PersonTable :information="information" @delete="deleteEntry" />
  <AddPerson @add="addPersonTable" />
  <OrderList />
  <GameList />
  <ListToGrid />
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
import ListToGrid from './components/listToGrid.vue'
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
            ListToGrid,
            Mystery8Ball
        },
        methods: {
            addPersonTable(event) {
                this.information.push(event)
            },
            deleteEntry(event) {
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
    display: grid;
	grid-template-columns: 1fr 1fr 1fr;
	grid-template-rows: 1fr 1fr 1fr;
}
.grid-component {
    max-height: 300px;
    padding: 1rem;
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

@media only screen and (max-width: 1300px) {
    body {
        transform: scale(80%);
        transform: translateY(1rem);
    }
    #app {
        display: inline;
    }
    .grid-component {
        padding: 1rem;
    }
    .time {
        font-size: 3rem;
    }
    .ball{
        transform: translateY(50rem);
    }
}
</style>
