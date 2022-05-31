<main>
    <DigitalClock />
    <LoginForm />
    <QuizTest />
    <PersonTable information = {information}/>
    <AddPerson on:newPerson = {addPersonToTable}/>
    <OrderList />
    <GameList />
    <Mystery8Ball />
</main>


<script>
    import DigitalClock from './components/digitalClock.svelte';
    import LoginForm from './components/loginForm.svelte';
    import QuizTest from './components/quizTest.svelte';
    import PersonTable from './components/personTable.svelte';
    import AddPerson from './components/addPerson.svelte';
    import OrderList from './components/orderList.svelte';
    import GameList from './components/gameList.svelte';
    import Mystery8Ball from './components/mystery8Ball.svelte';

  


    let information = [
            {
            firstName:'chik',
            lastName: 'sdasd',
            age: "22",
            },
            {
            firstName:'chike',
            lastName: 'sdasdsdsd',
            age: "55",
            }
            ]
 
    
    function addPersonToTable(e) {
            information = information.concat(e.detail.details)
  }
  
</script>


<style>
    main {
        transform: translateY(4rem);
        display: flex;
        flex-wrap: wrap;
        align-items: center;
        justify-content: center;
        text-align: center;
        }

    .toggle {
        position: fixed;
        top:0;
        right:0;
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