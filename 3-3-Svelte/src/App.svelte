<main>
    <DigitalClock />
    <LoginForm />
    <QuizTest />
    <PersonTable information = {information}/>
    <AddPerson on:newPerson = {addPersonToTable}/>
    <OrderList />
    <GameList />
    <ListToGrid />
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
import ListToGrid from './components/listToGrid.svelte';




let information = [
        {
        firstName: 'Perminder',
        lastName: 'Dhillon',
        age: 31,
        },
]


function addPersonToTable(e) {
        console.log(e)
        information = [...information, e.detail]
        console.log(information)
}

</script>


<style>
main {
	display: grid;
	grid-template-columns: 1fr 1fr 1fr;
	grid-template-rows: 1fr 1fr 1fr;
        max-height: 1px;
}


@media only screen and (max-width: 1300px) {
	main {
        transform: scale(80%);
        transform: translateY(1rem);
	}
	main {
        display: inline;
	}
}
</style>