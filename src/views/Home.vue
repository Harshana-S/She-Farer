<template>
  <div class="home">
      <div class="wrap-banner">
        <div class="main-title">
          <h2>
            <SignIn />
            <vue-typer text='Get Set Travel!'
              :repeat='infinity'
              :shuffle='false'
              initial-action='typing'
              :pre-type-delay='10'
              :type-delay='250'
              :pre-erase-delay='2000'
              :erase-delay='250'
              erase-style='backspace'
              :erase-on-complete='false'
              caret-animation='blink'            
            ></vue-typer>
          </h2>
          <br>
        </div>
        <vue-particles 
          color="#ff0000"
          :particleOpacity="0.7"
          linesColor="#000000"
          :particlesNumber="80"
          shapeType="circle"
          :particleSize="5"
          :linesWidth="2"
          :lineLinked="true"
          :lineOpacity="0.4"
          :linesDistance="150"
          :moveSpeed="3"
          :hoverEffect="true"
          hoverMode="grab"
          :clickEffect="true"
          clickMode="push"
        >
        </vue-particles>
      </div>
  </div>
</template>

<script>
// @ is an alias to /src
import { VueTyper } from 'vue-typer'
import SignIn from "@/components/SignIn.vue"

export default {
  name: "home",
  components: {
    VueTyper,
    SignIn
  }
};
</script>

<style>
body{
  background-color: rgb(3, 10, 10);
  overflow-y: hidden;
  -webkit-overflow-scrolling: hidden;
}
 .main-title {
    color: rgb(110, 6, 6);
    z-index: 999;
 }
.vue-typer {
  font-family: Copperplate, 'Copperplate Gothic Light', fantasy;
}

.vue-typer .custom.char.typed {
  color: #ff0000;
}
.particles-js {
    background-color: black;
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: -999;

}
  .wrap-banner {
    position: relative;
    -webkit-align-items: center;
    -ms-flex-align: center;
    align-items: center;
    display: -webkit-flex;
    display: flex;
    height: 100%;
    justify-content: center;
  }

</style>

