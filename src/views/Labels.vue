<template>
  <Layout>
    <ol class="tags">
      <li v-for="tag in tags" :key="tag">
        <span>{{tag}}</span>
        <Icon name="right"/>
      </li>

    </ol>
    <div class="createTag-wrapper">
      <button class="createTag" @click="createTag">New Label</button>
    </div>
  </Layout>
</template>

<script lang="ts">
  import Vue from 'vue';
  import {Component} from 'vue-property-decorator';
  import tagListModel from '@/models/tagListModel';
  import {parseForESLint} from '@typescript-eslint/parser';

  tagListModel.fetch();


  @Component({})
  export default class Labels extends Vue {
    tags = tagListModel.data;

    createTag() {
      const name = window.prompt('Please enter the name of Label');
      if (name) {
        const message = tagListModel.create(name);
        if (message === 'duplicated') {
          window.alert('Label duplicated');
        } else if (message === 'success') {
          window.alert('Label created success');
        }
      }
    }
  }
</script>

<style lang="scss" scoped>
  .tags {
    background: white;
    font-size: 16px;
    padding-left: 16px;

    > li {
      min-height: 44px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      border-bottom: 1px solid #99ccff;
    }

    svg {
      color: #666;
      width: 18px;
      height: 18px;
      margin-right: 16px;
    }
  }

  .createTag {
    background: #6699cc;
    border-radius: 4px;
    border: none;
    height: 40px;
    padding: 0 16px;

    &-wrapper {
      text-align: center;
      padding: 16px;
      margin-top: 44-16px;
    }
  }
</style>