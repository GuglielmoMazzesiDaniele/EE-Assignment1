<template>
  <div id="app" class="common-layout">
    <div class="sidebar">
      <!--      Fake left part (for layout)-->
    </div>
    <div id="main">

      <el-header>
        <h1>Welcome to the App</h1>
      </el-header>
      <el-main>
        <div v-if="currentStep === 1">
          <WelcomePage @next="goToForm"/>
        </div>
        <div v-if="currentStep === 2">
          <DemographicsForm @next="goToTasks"/>
        </div>
        <div v-if="currentStep === 3">
          <ExpTasks :remainingChoices="remainingChoices" @done="finish"/>
        </div>
        <div v-if="currentStep === 4">
          <h1>Thank you for completing the steps!</h1>
        </div>
      </el-main>

    </div>
    <div class="sidebar">
<!--      Fake right part -->
    </div>

  </div>
</template>

<script>
import WelcomePage from './components/WelcomePage.vue';
import DemographicsForm from './components/DemographicsForm.vue';
import ExpTasks from './components/ExpTasks.vue';


export default {
  name: 'App',
  components: {
    WelcomePage,
    DemographicsForm,
    ExpTasks
  },
  data() {
    return {
      currentStep: 1,  // Start at the welcome page
      remainingChoices: 10
    };
  },
  methods: {
    goToForm() {
      this.currentStep = 2;  // Move to form page
    },
    goToTasks() {
      this.currentStep = 3;  // Move to button selection
    },
    finish() {
      this.currentStep = 4;  // Final step, thank the user
    }
  }
};
</script>

<style>
.el-header {
  display: flex; /* Enable flexbox */
  justify-content: center; /* Center horizontally */
  align-items: center; /* Center vertically */
  text-align: center; /* Center text */
}
.el-main {
  display: flex; /* Enable flexbox */
  justify-content: center; /* Center horizontally */
  text-align: center; /* Center text */
}
#app {
    display: flex;
    width: 100vw;
    border: 1px solid black;
    height: 80vh;

}


.sidebar {
  border: 1px solid red;
  width: 25vw;
}
</style>
