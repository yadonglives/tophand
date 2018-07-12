<template>

  <!-- 跑马灯 start -->
  <Row>
    <Col span="24">
    <!--<Carousel v-model="carouselData" :height="400" loop>
      <CarouselItem v-for="item in carouselItems">
        <div :style="{backgroundImage:'url(' + item.img + ')', backgroundRepeat:'no-repeat', backgroundSize:'cover', height:'100%'}">{{item.title}}</div>
      </CarouselItem>
    </Carousel>-->

    </Col>
  </Row>
  <!-- 跑马灯 end -->
</template>

<script>
    export default {
      name: "home",
      data(){
        return {
          carouselData:0,
          carouselItems:[
            {
              img:'http://img5.imgtn.bdimg.com/it/u=2906706606,3286246755&fm=27&gp=0.jpg',
              title:'银河'
            },
            {
              img:'http://attachments.gfan.com/forum/201509/23/140610ebbookekbr1qbte1.jpg',
              title:'星空'
            },
            {
              img:'http://pic1.win4000.com/wallpaper/c/547824e3a599f.jpg',
              title:'森林'
            },
            {
              img:'http://img2.imgtn.bdimg.com/it/u=3421657713,305786063&fm=27&gp=0.jpg',
              title:'风之旅人'
            }
          ],
          selectName:1
        }
      },
      methods:{
        login(){
          this.$router.push({path:'/login'});
        },
        selected(name){
          this.$data.selectName = name;
          alert(this.$data.selectName);
        }
      }
    }
</script>

<style scoped>

</style>
