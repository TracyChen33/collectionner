<template>
  <Layout>
    <div class="tags">
      <router-link class="tag" v-for="tag in tags" :key="tag.id"
      :to="`/labels/edit/${tag.id}`">
        <span>{{tag.name}}</span>
        <Icon name="right"/>
      </router-link>

    </div>
    <div class="createTag-wrapper">
      <Button class="createTag" @click="createTag">New Label</Button>
    </div>
  </Layout>
</template>

<script lang="ts">
  import Vue from 'vue';
  import {Component} from 'vue-property-decorator';
  import tagListModel from '@/models/tagListModel';

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

    > .tag {
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