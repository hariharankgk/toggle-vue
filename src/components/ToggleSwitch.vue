<template>
  <div>
    <label class="toggle__switch">
      <input type="checkbox" @input="onInput" :disabled="disabled" :checked="checked">
      <span class="toggle__switch--slider toggle__switch--round"></span>
    </label>
  </div>
</template>

<script setup lang="ts">
  const props = defineProps({
    disabled: { type: Boolean, default: false },
    checked: { type: Boolean, default: false }
  })
  const changeEmitName = 'updateInput';
  const emits = defineEmits<{(e: typeof changeEmitName, id: string): void }>();
  const onInput = (event: Event) => {
    const target = event.target as HTMLInputElement;
    const checked = target.checked ? 'toggled-on' : 'toggled-off';
    emits(changeEmitName, checked);
  };
</script>

<style lang="scss">
.toggle__switch {
  position: relative;
  display: inline-block;
  width: 34px;
  height: 16px;

  .toggle__switch--slider {
    position: absolute;
    cursor: pointer;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: var(--grey2);
    -webkit-transition: .4s;
    transition: .4s;

    &:before {
      position: absolute;
      content: "";
      height: 8px;
      width: 8px;
      left: 4px;
      bottom: 4px;
      background-color: var(--white);
      -webkit-transition: .4s;
      transition: .4s;
    }

    &.toggle__switch--round {
      border-radius: 34px;
      &:before {
        border-radius: 50%;
      }
    }
  }

  input[type='checkbox'] { 
    opacity: 0;
    width: 0;
    height: 0;

    &:disabled~.toggle__switch--slider {
      background-color: var(--grey1);
    }

    &:checked~.toggle__switch--slider {
      background-color: var(--green);
    }

    &:focus~.toggle__switch--slider {
      box-shadow: 0 0 1px var(--green);
    }

    &:checked + .toggle__switch--slider:before {
      -webkit-transform: translateX(16px);
      -ms-transform: translateX(16px);
      transform: translateX(16px);
      width: 12px;
      height: 12px;
      top: 2px;
    }
  }
}
</style>
