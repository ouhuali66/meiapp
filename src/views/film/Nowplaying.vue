<template>
  <div>
    <ul>
      <!-- 必须要使用:key="item.id"来绑定key值 -->
      <li v-for="item in datalist" :key="item.filmId" @click="handleClick(item.filmId)">
        <img :src="item.poster"/>
        <h3>{{item.name}}</h3>
        <p>{{item.actors}}</p>
        <p>{{item.category}}</p>
      </li>
    </ul>
  </div>
</template>

<script>
// 安装axios并引入axios发送ajax请求数据  使用 npm install axios命令来安装axios
import axios from 'axios';
export default {
  data () {
    return {
      datalist: []
    }
  },
  methods: {
    // handleClick (id) {
    //   console.log(id)
    //   // location.href = '#/center'
    //   // 路径跳转  编程式导航, this.$router表示拿到的是路由对象
    //   // this.$router.push(`/detail/${id}`)

    //   // 路由名称跳转
    //   // this.$router.push({
    //   //   name: 'demoDetail',
    //   //   // 设置参数
    //   //   params: {
    //   //     myid: id
    //   //   }
    //   // })

    //   // 使用query实现路由跳转
    //   this.$router.push(`/detail?id=${id}`)
    // }
  },
  // 在mounted生命周期中发送ajax请求数据
  mounted() {
    axios({
      url:'https://m.maizuo.com/gateway?cityId=310100&pageNum=1&pageSize=10&type=1&k=3030777',
      headers: {
        'X-Client-Info': '{"a":"3000","ch":"1002","v":"5.0.4","e":"16184501213235970094727169","bc":"310100"}',
        'X-Host': 'mall.film-ticket.film.list'
      }
    }).then(res => {
      console.log(res.data.data.films)
      this.datalist = res.data.data.films
    })
  }
}
</script>

<style scoped>
* {
  margin:0;
  padding:0;
}
ul {
  list-style: none;
}
li {
  float: left;
  margin-top: 10px;
}
img {
  float: left;
  width: 100px;
  margin-right: 10px;
}
h3,p{
  float: right;
  font-size: 12px;
}
</style>

