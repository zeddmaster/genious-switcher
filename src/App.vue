<script setup>
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
import GeniousSwitcher from './components/GeniousSwitcher.vue'
import {ref} from 'vue';

const switcherValue = ref(0);

</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />
    </div>
  </header>

  <main>
    <GeniousSwitcher v-model="switcherValue">
      <div class="switcher-title">Switcher. Try!</div>
      <div class="switcher-value">value: {{ switcherValue }}</div>
    </GeniousSwitcher>
  </main>
</template>

<style scoped>

.switcher-title{
  font-weight: bold;
  font-size: 16px;
  line-height: 16px;
  margin-bottom: 6px;
}

.switcher-value{
  font-size: 13px;
  line-height: 13px;
  color: #555;
}

header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
