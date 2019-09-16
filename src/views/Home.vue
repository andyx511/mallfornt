<template>
  <el-container>
    <el-header>Header</el-header>
    <el-main>
      <el-carousel indicator-position="outside">
        <el-carousel-item v-for="item in 3" :key="item">
          <el-image
            style="width: 100%; height: 100%"
            :src="url"
            :fit="fit"></el-image>
        </el-carousel-item>
      </el-carousel>
      <el-row :gutter="20" style="height: 48px" >
        <el-col :span="4" v-for="(item, index) in 5" :key="item" :offset="index==0 ? 2 : 0">
          <el-card :body-style="{ padding: '0px' }" shadow="hover">
            <img src="https://shadow.elemecdn.com/app/element/hamburger.9cf7b091-55e9-11e9-a976-7f4d0b07eef6.png" class="image">
            <div >
              <span>好吃的汉堡</span>
              <div class="bottom clearfix">
                <time class="time">{{ currentDate }}</time>
                <div>{{item}}</div>
                  <el-button type="text" class="button" @click="check({item})">操作按钮</el-button>
              </div>
            </div>
          </el-card>
        </el-col>
      </el-row>
    </el-main>
    <el-footer>
      foot
      <div>{{list}}</div>
      <el-button @click="post">???</el-button>
    </el-footer>
  </el-container>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import axios from 'axios'
export default {
  name: 'home',
  data () {
    return {
      currentDate: new Date(),
      url: 'https://timgsa.baidu.' +
        'com/timg?image&quality=80&size=b' +
        '9999_10000&sec=1568532014571&di=' +
        'f4befa42fff652bb1c3b4db174997e1c&imgtype=0&src=http%3' +
        'A%2F%2Fimages.hisupplier.com%2F' +
        'var%2FuserImages%2F201801%2F11%2F145822673564_s.jpg',
      list: 'null'
    }
  },
  methods: {
    check (o) {
      console.log(o)
      this.$router.push({ path: '/about', query: { id: o } })
    },
    post () {
      axios.get('http://127.0.0.1:8080/product/list').then((res) => {
        this.list = res.data.data.list
      })
    }
  }
}
</script>
<style>
  .time {
    font-size: 13px;
    color: #999;
  }

  .bottom {
    margin-top: 13px;
    line-height: 12px;
  }

  .button {
    padding: 0;
    float: right;
  }

  .image {
    width: 100%;
    display: block;
  }

  .el-header, .el-footer {
    background-color: #B3C0D1;
    color: #333;
    text-align: center;
    line-height: 60px;
  }

  .el-aside {
    background-color: #D3DCE6;
    color: #333;
    text-align: center;
    line-height: 200px;
  }

  .el-main {

    text-align: center;
  }

  body > .el-container {
    margin-bottom: 40px;
  }

  .el-container:nth-child(5) .el-aside,
  .el-container:nth-child(6) .el-aside {
    line-height: 260px;
  }

  .el-container:nth-child(7) .el-aside {
    line-height: 320px;
  }
  .el-carousel__item h3 {
    color: #475669;
    font-size: 18px;
    opacity: 0.75;
    line-height: 300px;
    margin: 0;
  }

  .el-carousel__item:nth-child(2n) {
    background-color: #99a9bf;
  }

  .el-carousel__item:nth-child(2n+1) {
    background-color: #d3dce6;
  }
</style>
