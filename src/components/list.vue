<template>
  <div class="list">
    <ListItem 
      @removeTask="removeTask"
      v-for="item in dataList"
      :key="item.id"
      :item="item"
    />  
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
    padding: 10px 0 90px 0;
    background-color: #212121;
    height: calc(100vh - 100px);
  }

</style>