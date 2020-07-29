<template>
  <div class="app">
    <Interface 
      @addNewTask="addNewTask"
      @setSearchValue="setSearchValue"
    />
    <List 
      :dataList="activeList" 
      @removeTask="removeTask"
    />
  </div>
</template>

<script>
  import List from './components/list.vue';
  import Interface from './components/interface.vue';

  export default {
    name: 'app',
    data () {
      return {
        activeList: [{id: 0, description: 'Тестовое сообщение'}],
        dataList: [{id: 0, description: 'Тестовое сообщение'}],
        searchValue: ""
      }
    }, 
    components: {
      List, Interface
    },
    methods: {
      addNewTask(data) {
        this.dataList.push({id: this.dataList.length, description: data.text})
        this.checkSearchValue()
      },
      removeTask(data) {
        this.dataList.splice(data.id, 1);
        for(let i = data.id; i < this.dataList.length; i++) {
          this.dataList[i].id -= 1
        }
        this.checkSearchValue()
      },
      setSearchValue(data) {
        this.searchValue = data.value
        this.checkSearchValue()
      },
      checkSearchValue() {
        if(!!this.searchValue) {
          this.activeList = this.dataList.filter(task => task.description.includes(this.searchValue))
        } else {
          this.activeList = this.dataList
        }
      }
    }
  }
</script>

<style lang="scss">
  @import "~bootstrap/scss/bootstrap";

  .app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #100a1c;
  }

</style>
