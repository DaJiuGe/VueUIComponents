<template>
  <button class="v-button"><slot>确定</slot></button>
</template>

<script setup></script>

<style scoped>
  .v-button {
    background: rgb(18, 121, 212);
    color: #fff;
    width: 80px;
    height: 38px;
    border: none;
    outline: none;
    border-radius: 3px;
  }

  .v-button:hover {
    background: rgba(18, 121, 212, 0.8);
  }

  .v-button:active {
    background: rgb(21, 138, 240);
  }
</style>
