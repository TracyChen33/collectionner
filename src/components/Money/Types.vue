<template>
    <ul class="types">
      <li class="selected">Spend</li>
      <li>Income</li>
    </ul>
</template>

<script lang="ts">
  import Vue from 'vue';
  import {Component} from 'vue-property-decorator';

  @Component
  export default class Types extends Vue {

  }
</script>

<style lang="scss" scoped>

  .types {
    background: #6699cc;
    display: flex;
    text-align: center;
    font-size: 24px;

    > li {
      width: 50%;
      height: 64px;
      display: flex;
      justify-content: center;
      align-items: center;
      position: relative;

      &.selected::after {
        content: '';
        position: absolute;
        bottom: 0;
        left: 0;
        width: 100%;
        height: 4px;
        background: #333333;
      }
    }
  }


</style>