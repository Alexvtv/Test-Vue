<template>
  <div class="list">
    <ListItem 
      @removeTask="removeTask"
      v-for="item in dataList"
      :key="item.id"
      :item="item"
    />  
    <div class='corp-content'>
      <img src="./../assets/corp-image.png" /> 
      <img src="./../assets/corp-text.png" /> 
    </div>
  </div>
</template>

<script>
  import ListItem from './listItem.vue';
  export default {
    components: {
      ListItem
    },
    props: {
      dataList: {
        type: Array,
        required: true
      },
    },
    methods: {
      removeTask(data) {
        this.$emit('removeTask', {
          id: data.id
        });
      }
    }
  }
</script>

<style lang="scss">

  .list {
    position: relative;
    overflow-y: auto;
    padding: 10px 0 90px 0;
    background-color: #212121;
    height: calc(100vh - 100px);
    .corp-content {
      position: absolute;
      width: 270px;
      right: 20px;
      top: 20px;
      border: 2px solid #77ebdd;
      img {
        width: 100%
      }
    }
  }

  @media (max-width: 834px) {
    .list {
      .corp-content {
        width: 200px;
      }
    }
  }

  @media (max-width: 634px) {
    .list {
      .corp-content {
        display: none;
      }
    }
  }

</style>