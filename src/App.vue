<template>
<div class="container">
	
  <h1>STAY ORGANIZED...</h1>

  <div class="container_app">
    <Header
      @toggle-add-task="toggleAddTask"
      title="Todo-App"
      :showAddTask="showAddTask"
    />
    <router-view :showAddTask="showAddTask"></router-view>
    <Footer />
  </div>
</div>

</template>
 
<script>
import Header from "./components/Header";
import Footer from "./components/Footer";


export default {
  name: "App",
  components: {
    Header,
    Footer,
  },
  data() {
    return {
      tasks: [],
      showAddTask: false,
    };
  },
    methods: {
    toggleAddTask() {
      this.showAddTask = !this.showAddTask;
    },
  },


  
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap");
@import url('https://fonts.googleapis.com/css2?family=Permanent+Marker&display=swap');
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: "Poppins", sans-serif;
  background-image: url('./assets/agenda.jpg');
  background-attachment: fixed;
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
  
}

.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  min-height: 100vh;
}

.container h1 {
  margin-top:auto;
  color: white;
  font-family: 'Permanent Marker', cursive;
}
.container_app {
  min-width: 50vw;
  min-height: 100%;
  margin: auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
  background-color:rgba(255,255,255,0.7);
}

.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}

.btn:focus {
  outline: none;
}

.btn:active {
  transform: scale(0.98);
}

.btn-block {
  display: block;
  width: 100%;
}
</style>