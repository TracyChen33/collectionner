<template>
  <Layout>
    <div class="navBar">
      <Icon class="leftIcon" name="left"/>
      <span class="title">EditLabel</span>
      <span class="rightIcon"></span>
    </div>
    <div class="form-wrapper">
      <FormItem filed-name="Label Name"
                placeholder="Please enter the Label Name"/>
    </div>
<div class="button-wrapper">
  <Button>Delete Label</Button>
</div>

  </Layout>

</template>

<script lang="ts">
  import Vue from 'vue';
  import {Component} from 'vue-property-decorator';
  import tagListModel from '@/models/tagListModel';
  import FormItem from '@/components/Money/FormItem.vue';
  import Button from '@/components/Button.vue';

  @Component({
    components: {Button, FormItem}
  })
  export default class EditLabel extends Vue {
    created() {
      const id = this.$route.params.id;
      tagListModel.fetch;
      const tags = tagListModel.data;
      const tag = tags.filter(t => t.id === id);
      if (tag) {
        console.log(tag);
      } else {
        this.$router.replace('/404');
      }


    }


  }
</script>

<style lang="scss" scoped>
  .navBar {
    text-align: center;
    font-size: 16px;
    padding: 12px 16px;
    background: white;
    align-items: center;
    justify-content: space-between;
    display: flex;

    > .title {

    }

    > .leftIcon {
      width: 24px;
      height: 24px;
    }

    > .rightIcon {
      width: 24px;
      height: 24px;
    }
  }

  .form-wrapper {
    background: white;
    margin-top: 8px;
  }
.button-wrapper{
  text-align: center;
  padding: 16px;
  margin-top: 44-16px;

}
</style>