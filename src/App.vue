<template>
  <div id="app">
      <h1>Problema de Monty Hall</h1>
      <form class="form">
          <div v-if="!started">
              <label for="portsAmount">Quantas portas? </label>
              <input type="number" id="portsAmount" size="3" max="10" min="1"
                v-model.number="portsAmount" required>
          </div>
          <div v-if="!started">
              <label for="selectedPort">Qual porta é premiada? </label>
              <input type="number" id="selectedPort" size="3" required :max="portsAmount" min="1"
                v-model.number="selectedPort">
          </div>
          <input v-if="!started" @click="started = true && selectedPort > 0 && selectedPort <= portsAmount" type="submit" value="Iniciar">
          <button v-if="started" @click="started = false">Reiniciar </button>
      </form>
      <div class="doors" v-if="started">
          <div v-for="i in portsAmount" :key="i">
              <Door :hasGift="i === selectedPort" :number="i"/>
          </div>
      </div>
  </div>
</template>

<script>
    import Door from './components/Door.vue';
    export default {
        name: 'App',
        components: { Door },
        data: function() {
            return {
                started: false,
                portsAmount: 3,
                selectedPort: 1
            } 
        }
    }
</script>

<style>
    html{
        width: 100vw;
        height: 100vh;
    }
    * {
        box-sizing: border-box;
        font-family: 'Montserrat',sans-serif;
    }
    body{
        margin: 0px;
        width: 100%;
        height: 100%;
        display: flex;
        justify-content: center;
        color: #FFF;
        background: linear-gradient(to right, rgb( 21, 153, 87), rgb( 21, 87, 153));
    }
    #app {
        /* width: 100%; */
        /* height: fit-content; */
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }
    #app h1 {
        /* border: 1px solid #000; */
        background-color: #0004; 
        /* padding: 20px; */
        /* margin-bottom: 60px; */
    }
    .form {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        /* margin-bottom: 40px; */
    }
    .form, .form input, .form button {
        /* margin-bottom: 10px; */
        /* font-size: 2rem; */
    }
    .doors{
        width: 100vw;
        align-self: stretch;
        display: flex;
        justify-content: space-around;
        flex-wrap: wrap;
    }
    *{
        --base-resolution: 1920;
        --actual-resolution: 360
    }
    @media (min-width: 400px) {
        *{
            --actual-resolution: 400;
        }
    }
    @media (min-width: 640px) {
        *{
            --actual-resolution: 640;
        }
    }
    @media (min-width: 1024px) {
        *{
            --actual-resolution: 1024;
        }
    }
    @media (min-width: 1360px) {
        *{
            --actual-resolution: 1360;
        }
    }
    @media (min-width: 1920px) {
        *{
            --actual-resolution: 1920;
        }
    }
    *{
        --mult-factor: calc(var(--actual-resolution)/var(--base-resolution) * 1.5);
    }
    @media (orientation: portrait) {
        *{
            --mult-factor: calc(var(--actual-resolution)/var(--base-resolution) * 2.5);
        }
    }
    *{
        --app-h1-border: calc(1px * var(--mult-factor));
        --app-h1-padding: calc(20px * var(--mult-factor));
        --app-h1-margin-bottom: calc(60px * var(--mult-factor));
        --form-margin-bottom: calc(10px * var(--mult-factor));
        --font-size-1: calc(2rem * var(--mult-factor));
        --form-input-button-border-size: calc(0.1rem * var(--mult-factor));
        --form-input-button-border-radius: calc(6px * var(--mult-factor));
    }
    #app h1 {
        border: var(--app-h1-border) solid #000;
        padding: var(--app-h1-padding);
        margin-bottom: var(--app-h1-margin-bottom);
        font-size: var(--font-size-1);
    }
    .form, .form input, .form button {
        margin-bottom: var(--form-margin-bottom);
        font-size: var(--font-size-1);
    }
    /* .form input, .form button{
        border: var(--form-input-button-border-size) solid gray;
        border-radius: var(--form-input-button-border-radius);
        
    } */
</style>