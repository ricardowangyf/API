<template>
  <div>
      <!-- {{userList}} -->
    <!-- <div v-for="item in userList" :key="item.id">
      <div>{{ item.userList }}</div>
    </div> -->

    <!-- <div>
      {{obj}}
      <div>{{obj.id }}</div>
      <div>{{obj.username }}</div>
      <div>{{obj.sex }}</div>
    </div> -->
    <!-- <div>
      <div>{{asdas.id }}</div>
      <div>{{asdas.username }}</div>
      <div>{{asdas.sex }}</div>
    </div> -->

    <!-- <div>
      <div v-for="item in items" :key="item.items">
        {{items}}
      </div>
    </div> -->
    <!-- <div>
      <div>
        {{statusmess.status}}
      </div>
    </div> -->
    <div>
      {{classname.id}}
      {{classname.owner}}
      {{classname.repo}}
      {{classname.ref}}
      {{classname.path}}
    </div>
  </div>  
</template>

<script>
import { reqCategoryList } from '../API/index'
export default {
  data() {
    return {
      userList: [],
      obj:{},
      items:{},
      statusmess:[],
      classname:[]
    }
  },
  mounted() {
    // this.userList = 
    // [{
    //   id: 1,
    //   username: 'x',
    //   sex: 123123
    //   }]
    // reqCategoryList().then((data) => {
    //   console.log(data.data)
    //   this.userList = data.data
    // })
    // reqCategoryList().then((data) => {
    //   console.log(data.data)
    //   this.obj = data.data
    // })
    // reqCategoryList().then((data) => {
    //   console.log(data.data)
    //   this.items = data.data
    // })
    // reqCategoryList().then((data) => {
    //   console.log(data.data)
    //   this.statusmess = data.data
    // })
    reqCategoryList().then((data) => {
      console.log(data.data)
      this.classname = data.data
    })
  }
};


</script>

<style>
</style>