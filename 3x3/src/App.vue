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
</template>

<script>
import digitalClock from './components/digitalClock.vue'
import loginForm from './components/loginForm.vue'
import quizTest from './components/quizTest.vue'
import PersonTable from './components/personTable.vue'
export default {
    name: "App",
    components: { digitalClock, loginForm, quizTest, PersonTable }
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
