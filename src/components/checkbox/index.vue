<template>
  <label
    :for="checkId"
    class="su-checkbox__wrapper"
    :class="{ 'su-checkbox-checked': checked }"
    :checked="checked"
    @click="emit('update:checked', !checked)"
  >
    <span class="su-checkbox">
      <input
        type="checkbox"
        :id="checkId"
        class="su-checkbox__input"
        v-model="checked"
      />
      <div class="su-checkbox__inner"></div>
    </span>
    <span class="su-checkbox__text">
      <slot></slot>
    </span>
  </label>
</template>

<script lang="ts" setup>
  import { ref } from 'vue'
  import { nanoid } from 'nanoid'

  defineProps({
    checked: Boolean
  })
  const emit = defineEmits(['update:checked'])
  const checkId = ref(nanoid())
</script>

<style lang="scss">
  .su-checkbox__wrapper {
    display: inline-block;
    position: relative;
    cursor: pointer;
  }

  .su-checkbox {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
    position: relative;
    display: inline-block;
    white-space: nowrap;
    outline: none;
    vertical-align: middle;

    .su-checkbox__input {
      position: absolute;
      top: 0;
      left: 0;
      bottom: 0;
      right: 0;
      margin: 0;
      width: 100%;
      height: 100%;
      z-index: 1;
      cursor: pointer;
      opacity: 0;
    }

    .su-checkbox__inner {
      position: relative;
      top: 0;
      left: 0;
      width: 16px;
      height: 16px;
      background-color: #fff;
      border: 1px solid #d9d9d9;
      border-radius: 3px;
      transition: all 0.3s;

      &::after {
        content: '';
        position: absolute;
        top: 46%;
        left: 22%;
        width: 4px;
        height: 9px;
        border: 2px solid #fff;
        border-top: 0;
        border-left: 0;
        transform: rotate(45deg) scale(0) translate(-50%, -50%);
        opacity: 0;
        transition: all 0.1s ease-in-out, opacity 0.1s;
      }
    }
  }

  .su-checkbox-checked {
    .su-checkbox__inner {
      background-color: #267926;
      border-color: #267926;
    }

    .su-checkbox__inner::after {
      transform: rotate(45deg) scale(1) translate(-50%, -50%);
      opacity: 1;
    }
  }

  .su-checkbox__text {
    display: inline-block;
    margin-left: 5px;
    vertical-align: middle;
  }
</style>
