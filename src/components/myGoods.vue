<template>
  <div class="my-goods-item">
    <div class="left">
      <div class="custom-control custom-checkbox" >
        <input type="checkbox" class="custom-control-input right-inp" :id="gObj.id" v-model="gObj.goods_state"
        >
        <label class="custom-control-label" for="gObj.id">
          <img :src="gObj.goods_img" alt="">
        </label>
      </div>
    </div>
    <div class="right">
      <div class="top">{{ gObj.goods_name }}</div>
      <div class="bottom">
        <span class="price">¥ {{ gObj.goods_price}}</span>
        <span>
           <my-count :obj="gObj"></my-count>
        </span>
      </div>
    </div>
  </div>
</template>

<script>
import MyCount from './myCount.vue'
export default {
    components:{
        MyCount
    },
    props:{
        gObj: Object
    }
}
</script>

<style lang="less" scoped>
.my-goods-item {
  display: flex;
  padding: 10px;
  border-bottom: 1px solid #ccc;
  .left {
    img {
      width: 120px;
      height: 120px;
      margin-right: 8px;
      border-radius: 10px;
    }
    .custom-control-label::before,
    .custom-control-label::after {
      top: 10px;
    }
  }
  .right {
    flex: 1;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    .top{
        font-size: 14px;
        font-weight: 700;
    }
    .bottom {
      display: flex;
      justify-content: space-between;
      padding: 5px 0;
      align-items: center;
      .price {
        color: red;
        font-weight: bold;
      }
    }
  }
  .right-inp{
      margin-right: 15px;
  }
}

</style>