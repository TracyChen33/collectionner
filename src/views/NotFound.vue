<template>
  <div>
    <div>Sorry,the page does not exist,Please check your web link</div>
    <div>
      <router-link to="/">Back to home page</router-link>
    </div>
  </div>
</template>

<script lang="ts">
  import Vue from 'vue';
  import {Component} from 'vue-property-decorator';

  @Component
  export default class NotFound extends Vue {

  }
</script>

<style lang="scss" scoped>

</style>