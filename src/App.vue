<template>
  <div class="toggle">
    <ToggleSwitch :checked="false" @updateInput="getValue" />
    <ToggleSwitch :checked="true"  @updateInput="getValue" />
    <ToggleSwitch :disabled="true" />
  </div>
</template>

<script setup lang="ts">
  import ToggleSwitch from './components/ToggleSwitch.vue'
  function getValue(val='') {
    console.log(val)
  }
</script>

<style lang="scss">
  :root {
    --grey1: rgba(0, 0, 0, 0.1);
    --grey2: rgba(0, 0, 0, 0.2);
    --pink: #9747FF;
    --green: #518D6C;
    --white: #FFFFFF;
  }
  
  
  .toggle {
    display: flex;
    justify-content: space-around;
    border:1px dashed var(--pink);
    align-items: center;
    border-radius: 5px;
    padding: 10px;
    width: 222px;
    height: 56px;
  }
</style>
