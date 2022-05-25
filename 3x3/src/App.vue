<template>
Digital Clock
<digitalClock />
<br/>
<br/>
Login Form (p)
<loginForm />
<br/>
<br/>
Multiple Choice Quiz
<quizTest />
<br/>
<br/>
Person Table
<personTable />
<br/>
<br/>
Order List
<orderList />
</template>

<script>
import digitalClock from './components/digitalClock.vue'
import loginForm from './components/loginForm.vue'
import quizTest from './components/quizTest.vue'
import personTable from './components/personTable.vue'
import orderList from './components/orderList.vue'
export default {
    name: "App",
    components: { digitalClock, loginForm, quizTest, personTable, orderList}
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
}
</style>
