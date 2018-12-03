<template>
 <div class="wrapper" >
      <swiper :indicator-dots="indicatorDots"
              :autoplay="autoplay" 
              :interval="interval" 
     		  :duration="duration" 
     		  :circular="circular" 
     		  :vertical="vertical"
     		  @change="swiperChange"
     		  @animationfinish="animationfinish">

     	<swiper-item>
          	<home-header :index="index"></home-header>
        </swiper-item>
        <!-- <swiper-item  v-for="item in list" :key="index">
          	<div class="swiper-content">
	            <image :class="imgAnimate" :src="item.imgUrl" />
	            <p  :class="[titleAnimate]">
	            	{{item.title}}<br>
	            	{{item.title1}}<br>
					{{item.title2}}<br>
					{{item.title3}}<br>
	            </p>
             </div>
        </swiper-item>-->
        <swiper-item>
          	<div class="swiper-content">
	            <image :class="imgAnimate" src="./static/img/img2.jpg" />
	            <p  :class="[titleAnimate]">
	            	No.1 ><br>
	            	早起，给妈妈一个拥抱<br>
	            	送一枝康乃馨<br>
					亲口和妈妈说一声：“妈妈，我爱你”<br>
					
	            </p>
             </div>
        </swiper-item>
         <swiper-item>
          	<div class="swiper-content">
	            <image :class="imgAnimate" src="./static/img/img3.jpg" />
	            <p  :class="[titleAnimate]">
	            	No.2 ><br>
	            	从今天开始<br>
	            	每年的今天<br>
					都与妈妈自拍一张<br>
					
	            </p>
             </div>
        </swiper-item>
         <swiper-item>
          	<div class="swiper-content">
	            <image :class="imgAnimate" src="./static/img/img4.jpg" />
	            <p  :class="[titleAnimate]">
	            	No.3 ><br>
	            	当天家务全包<br>
	            	洗菜、做饭、洗衣服、搞卫生<br>
					为妈妈洗洗脚、捶捶背<br>
					
	            </p>
             </div>
        </swiper-item>
         <swiper-item>
          	<div class="swiper-content">
	            <image :class="imgAnimate" src="./static/img/img5.jpg" />
	            <p  :class="[titleAnimate]">
	            	No.4 ><br>
	            	拿出以前拍的照片<br>
	            	和妈妈一起回忆<br>
					制作属于我们的青春纪念册<br>
					
	            </p>
             </div>
        </swiper-item>
         <swiper-item>
          	<div class="swiper-content">
	            <image :class="imgAnimate" src="./static/img/img6.jpg" />
	            <p  :class="[titleAnimate]">
	            	No.5 ><br>
	            	健康是最大的财富<br>
	            	陪妈妈做个身体检查<br>
					为妈妈做一顿饭<br>
					
	            </p>
             </div>
        </swiper-item>
         <swiper-item>
          	<div class="swiper-content">
	            <image :class="imgAnimate" src="./static/img/img7.jpg" />
	            <p  :class="[titleAnimate]">
	            	No.6 ><br>
	            	出门在外的伙伴们<br>
	            	给妈妈打个电话<br>
					慈母手中线，游子<br>
					
	            </p>
             </div>
        </swiper-item>
          <swiper-item>
          	<div class="swiper-content">
	            <image :class="imgAnimate" src="./static/img/img10.jpg" />
	            <p  :class="[titleAnimate]">
	            	No.7 ><br>
	            	感谢母亲的养育情<br>
	            	愿母亲每一天都平安愉悦<br>
					祝福母亲健康长寿<br>
					
	            </p>
             </div>
        </swiper-item>
      </swiper>
  </div>
</template>
<script>
import Fly from 'flyio/dist/npm/wx'
import HomeHeader from './HomeHeader'
export default {
 data() {
       return{
        list:[],
        imgAnimate:"",
        titleAnimate:"",
        index:100,
	    indicatorDots: false,
	    autoplay: true,
	    interval: 6000,
	    duration: 2500,
	    circular: true,
	    vertical:true
       }
      },
      components:{
      	HomeHeader
      },
      watch:{
        index (){
    	
            if(this.index !=0){
               this.imgAnimate="imgAnimate"
               this.titleAnimate="titleAnimate"
              setTimeout(()=>{this.imgAnimate="",this.titleAnimate=""},2000)
            }
            
          }
      },
      methods:{
        getQueryData (){
        	var fly = new Fly;
        	fly.config.baseURL='http://192.168.10.35:8090/static';
        	var _this = this;
       		fly.get("homedata.json").then((d)=>{
       			_this.list = d.data.data.list;
       		});
      },
	  animationfinish(e) {
	  		this.index = e.mp.detail.current;
    }
  },mounted (){
        //this.getQueryData();
      }
 
}
</script>
<style lang="scss" scoped>
.wrapper{
	height:100%;
	width:100%;
	margin-top: 0;
	background-image: url('https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1543321580270&di=a5191a71026433924f97e32a728d7221&imgtype=0&src=http%3A%2F%2Fimgsrc.baidu.com%2Fimgad%2Fpic%2Fitem%2F5882b2b7d0a20cf43020aee37d094b36acaf995d.jpg');
	swiper{
		height:100%;
	}
}

.swiper-content{
	height:100%;
	width:100%;
	image {
		 position: static;
		 padding:0.2rem;
		 width:95%;
		 height:6rem;
	}
	p{
         position: absolute;
         bottom:2.5rem;
		 color:#FFE159;
		 font-size:0.4rem;
		 text-shadow:0.1rem 0.2rem 0.4rem #6B361B;
		 font-weight: bold;
         padding-left:0.5rem;
         line-height: 0.6rem;
         padding-top: 0.5rem;
	}
}
  .imgAnimate{
    animation: imgmove 3s ease-in-out 1 forwards;
   -webkit-animation:imgmove 3s ease-in-out  1 forwards;
  }
  .titleAnimate{
   animation: titlemove 3s linear 1 forwards;
   -webkit-animation:titlemove 3s  linear 1 forwards;
  }
 
  @keyframes imgmove{
    0%{
      opacity: 0;
      transform: rotate(0deg) scale(1);
      -webkit-transform: rotate(0deg) scale(1);
    }
    20%{
    	opacity: 0.4;
        transform: rotate(45deg) scale(0.4);
        -webkit-transform: rotate(45deg) scale(0.4);
    }
   40%{
   	 	opacity: 1;
        transform: rotate(65deg) scale(2);
        -webkit-transform: rotate(65deg) scale(2);
    }
    80%{
       transform: rotate(30deg) scale(0.5);
      -webkit-transform: otate(30deg) scale(0.5);
    }
     90%{
       transform: rotate(5deg) scale(0.7);
      -webkit-transform:  rotate(5deg) scale(0.7);
    }
    
  }
  @keyframes titlemove{
    0%{
      left:1rem;
      bottom:0.2rem;
    }
    40%{
        right:0;
        bottom:3rem;
    }
    60%{
        left:0rem;
        bottom:3rem;
    }
}


</style>
