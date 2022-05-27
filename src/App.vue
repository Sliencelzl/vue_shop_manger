<template>
  <div id="app">
    <my-header background="red" color title="我的购物车"></my-header>
    <div class="main">
      <my-goods v-for="obj in list" :key="obj.id"  :gObj="obj"></my-goods>
    </div>
    <my-footer @changeAll="changeFn" :arr="list"></my-footer>
  </div>
</template>

<script>

import MyHeader from './components/myHeader.vue'
import MyGoods from './components/myGoods.vue'
import MyFooter from './components/myFooter.vue'
export default {
  name: 'App',
  components: {
    MyHeader,MyGoods,MyFooter
  },
  data(){
    return{
      list:[]
    }
  },
  created(){
    this.$axios({
      url:'/api/cart',
      method:"Get"
    }).then(res=>{
      this.list = res.data.list
      console.log(this.list)
    })
  },
  methods:{
    changeFn(bool){
      this.list.forEach(obj=>obj.goods_state = bool)
    }
  }
}
</script>

<style>
.main{
  padding-top: 45px;
  padding-bottom: 50px;
}
</style>
