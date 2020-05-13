<template>
  <nav>
    <router-link to="/money" class="item">
      <icon name = "money" class="icon"/>
      Money
    </router-link>

    <router-link to="/labels" class="item">
      <icon name = "label" class="icon" />
      Labels
    </router-link>

    <router-link to="/statistics" class="item">
      <icon name = "statistics" class="icon"/>
      Labels
    </router-link>
  </nav>
</template>

<script lang="ts">
  import Vue from 'vue';
  import {Component} from 'vue-property-decorator';

  @Component({
  })
  export default class Nav extends Vue {

  }
</script>

<style lang="scss" scoped>
  @import "~@/assets/style/helper.scss";
  nav {
    @extend %outerShadow;
    display: flex;
    flex-direction: row;
    font-size: 12px;
    >.item{
      padding: 2px 0;
      width: 33.33333%;
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
      .icon{
        width: 32px;
        height: 32px;
      }
    }
    > .item.selected{
      color:$color-highlight;
    }
  }

</style>