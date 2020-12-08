<template>
  <b-col class="mb-3 d-flex justify-content-center">
    <div class="flip-card">
      <div class="flip-card-inner">
        <div class="flip-card-front">
          <b-icon-question-square-fill font-scale="15"/>
        </div>
        <div class="flip-card-back">
          <h1>{{title}}</h1>
          <b-icon :icon="iconName" class="icon-center" font-scale="4"/>
          <p>{{description}}</p>
        </div>
      </div>
    </div>
  </b-col>
</template>

<script>
export default {
  title: 'StorageExample',
  color: "#FFFFFF",
  iconName: "key",
  description: "Description",
  props: {
    title: String,
    color: String,
    iconName: String,
    description: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .icon-center{
    width: auto;
    margin: 0px auto;
    display: block;
  }
  .flip-card {
    background-color: transparent;
    width: 300px;
    height: 300px;
    perspective: 1000px; /* Remove this if you don't want the 3D effect */
  }

  /* This container is needed to position the front and back side */
  .flip-card-inner {
    position: relative;
    width: 100%;
    height: 100%;
    transition: transform 0.8s;
    transform-style: preserve-3d;
  }

  /* Do an horizontal flip when you move the mouse over the flip box container */
  .flip-card:hover .flip-card-inner {
    transform: rotateY(180deg);
  }

  /* Position the front and back side */
  .flip-card-front, .flip-card-back {
    position: absolute;
    width: 100%;
    height: 100%;
    -webkit-backface-visibility: hidden; /* Safari */
    backface-visibility: hidden;
  }

  /* Style the back side */
  .flip-card-back {
    background-color: lightblue;
    text-align: center;
    color: white;
    display: flex;
    justify-content: center;
    flex-direction: column;
    border-radius: 10%;
    transform: rotateY(180deg);
  }
</style>
