<template>
  <div id="app">
    <div class="header">
      <h3>
        <b>Vue Jsss To do App</b>
      </h3>

      <hr />

    </div>




    <listForm /> 


    


  </div>
</template>

<script>
import listForm from "./components/HelloWorld"; 
export default {
  name: "Wtf", 
  components: {
    listForm, 
  }


}
</script>

<style>

*{
    font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif

}


.header{
  margin-left: 20px;
}


#app {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}



</style>
