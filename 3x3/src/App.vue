<template>
  <digitalClock />
  <loginForm />
  <quizTest />
  <personTable :information="information"/>
  <addPerson @add="addPersonTable"/>
  <orderList />
  <gameList />
  <mystery8Ball />
</template>

<script>
  import digitalClock from './components/digitalClock.vue'
  import loginForm from './components/loginForm.vue'
  import quizTest from './components/quizTest.vue'
  import personTable from './components/personTable.vue'
  import addPerson from './components/addPerson.vue'
  import orderList from './components/orderList.vue'
  import gameList from './components/gameList.vue'
  import mystery8Ball from './components/eightBall.vue'

  export default {
      name: "App",
      components: { digitalClock,
                    loginForm, 
                    quizTest, 
                    personTable, 
                    addPerson, 
                    orderList, 
                    gameList, 
                    mystery8Ball
                  },
      methods: {
          addPersonTable(event) {
              this.information.push(event)
              console.log(this.information)
      }
    },
     data(){
        return{
            information:[
                {
                firstName:'chik',
                lastName: 'sdasd',
                age: 22,
                },
                {
                firstName:'chike',
                lastName: 'sdasdsdsd',
                age: 55,
                }
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
        #app{
            display: inline;
        }
        .grid-component{
            padding: 5rem;
        }
        .time{
            transform: scale(3);
        }
        .items-list{
            display: inline;
        }
}
</style>
