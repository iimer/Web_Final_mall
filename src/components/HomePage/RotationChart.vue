<template>
  <div class="RotationChart">
    <el-carousel indicator-position="outside">
      <el-carousel-item v-for="item in imgUrl" :key="item">
        <router-link to=""><img :src="item" alt=""></router-link>
      </el-carousel-item>
    </el-carousel>
  </div>
</template>

<script>
export default {
  name: 'RotationChart',
  data () {
    return {
      imgUrl: []
    }
  },
  created () {
    this.$http({
      method: 'post',
      url: '/rotation_img'
    })
      .then((res) => {
        console.log(res)
        this.imgUrl = res.data
        console.log(this.imgUrl)
      })
      .catch((error) => {
        console.log(error)
      })
  }
}
</script>

<style>
.el-carousel__item h3 {
  color: #475669;
  font-size: 18px;
  opacity: 0.75;
  line-height: 300px;
  margin: 0;
}

.RotationChart{
  width: 540px;
  margin: 0 auto;
}
img{
  width: 540px;
  height: 300px;
}
</style>
