<template>
    <div class="main">
      <div class="list">
      <label for="title">Title</label>
      <input type="text" id="title" v-model="title">

      <label for="title">Project</label>
      <input type="text" id="title" v-model="project">

      <button @click="add()" id = "Add">Add</button>
      <lottie-player src="https://assets8.lottiefiles.com/packages/lf20_BF6OFq.json"  background="transparent"  speed="1"  style="width: 300px; height: 300px;"  loop controls autoplay></lottie-player> 
    </div>

      <h2>Pendings Lists</h2> 


      <div v-if="modal" class="tf">
               <Lottie :options="defaultOptions" :height="400" :width="400" v-on:animCreated="handleAnimation"/>

      </div>

    <div class="display">
      <ul>
        <router-link to="/detail" class="link">
        <li :key="todo" v-for="(todo,i) in existingApp" class="pending">
          <div> {{i+1}} {{todo.text}}</div> 
          <div class="project"> Project : {{todo.project}}</div>
          <div class="delete"> 
            <ion-icon class="icon" name="trash-outline" @click="deleteX(i)"></ion-icon>
          </div>


          <div @click = "done()" id = "status" class="status" v-bind:class="{already:todo.pending}">
            Pending
          </div>
        </li>

        </router-link>
      </ul>
    </div>
    </div>
</template>

<script>
import Vue from 'vue'
  import Lottie from './lottie.vue';
  import animationData from '@/assets/cube.json';
export default {
  name: "app", 
  components: {
    Lottie
  }, 
  data () {
     return {
       title: '', 
       project: '', 
       pending: false, 
       existingApp: [
         {
           text: "Have Sex", 
           project: "PornHub", 
           pending: false, 
         }, 
       ],

        defaultOptions: {animationData: animationData},
        animationSpeed: 1
     }

     
  },

  methods: {
    add(){
      this.existingApp.push({
        text: this.title, 
        project: this.project, 
        pending: false, 

      })



    }, 

    deleteX(i){
      this.existingApp.splice(i,1)
    }, 
    done(){
      alert("Done")
    },

    handleAnimation: function (anim) {
        this.anim = anim;
      },

      stop: function () {
        this.anim.stop();
      },

      play: function () {
        this.anim.play();
      },

      pause: function () {
        this.anim.pause();
      },

      onSpeedChange: function () {
        this.anim.setSpeed(this.animationSpeed);
      }
  } 

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.main {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-content: center;
}

#Add {
  outline: none;
  background-color: orange;
  border: none;
  border-radius: 10px;
  padding: 10px;
  margin-top: 10px;
}
.delete{
  display: flex;
  justify-content: flex-end;
  font-size: 20px;
}

.link {
  color: black;
}

.already {
  color: green;
}

.icon {
  cursor: pointer;
}
.pending {
  width: 200px;
  height: 100px;
  padding: 10px;
  border-radius: 10px;
  font-size: 15px;
  border: 2px solid rgb(237,237,237);
  font-weight: bold;
  line-height: 20px;
  position: relative;
  margin-bottom: 10px;
}
.status{
  padding: 10px 0;
  text-align: center;
  border: 1px solid red;
  width: 99%;
  border-radius: 10px;
  color: red;
  cursor: pointer;
}

#status{
  position: absolute;
  bottom: 0;
  left: 0;
}
.project {
  opacity: 0.4;
}
ul {
  list-style: none;
}
#Add:active {
  transform: translateY(-5px);
}
.list {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin-left: 40px;
}

.list > input {
  border-radius: 10px;
  outline: none;
  border: 1px solid aqua;
  padding: 10px; 
  width: 200px;
}

label {
  margin-right: 10px;
}
</style>
