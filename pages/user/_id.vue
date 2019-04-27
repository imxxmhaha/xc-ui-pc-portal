<template>
  <div>
    <!--这个页面会得到一个id参数-->
      修改用户信息{{id}},名称:{{name}}
  </div>
</template>

<script>
  export default {
    layout:'test',
    // 通过服务端渲染
    async  asyncData(){
      // 请求服务端接口
      // alert(0)  是无法在服务端运行的
      console.log("请求服务端接口...");

      //先调用a方法
      var a= await new Promise(function (resolve, reject) {
        setTimeout(function () {
          //alert(1)
          console.log(1)
          resolve(1)
        },2000)
      })
      //再调用b方法
      var b = await new Promise(function (resolve, reject) {
        setTimeout(function () {
          //alert(2)
          console.log(2)
          resolve(2)
        },1000)
      })
      return {
        name:'小鸣哥'
      }


    },
    data(){
      return {
        id : ''
      }
    },
    methods:{
      a(){
        return new Promise((resolve,reject)=>{
          setTimeout(()=>{
            // alert(1)
            resolve(1)
          },2000)
        })
      },
      b(){
        return new Promise((resolve,reject)=>{
          setTimeout(()=>{
            // alert(2);
            resolve(2)
          },1000)
        })
      }
    },
    mounted(){
      this.id = this.$route.params.id;
      console.log(this.id);
      // this.a().then(res=>{
      //   alert(res);
      // })
      //
      // this.b().then(res=>{
      //   alert(res);
      // })

    }
  }
</script>

<style>

</style>
