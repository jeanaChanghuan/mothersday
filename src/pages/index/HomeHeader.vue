<template>
	<div class="swiper-header">
            <image :class="[imgAnimate]"  src="./static/img/img1.png"/>
	  		<p :class="[title1Animate]">母亲，世界上最伟大的女性</p>
			<p :class="[title2Animate]">今天，我们为母亲做7件事</p>
			<!--https://tts.baidu.com/text2audio?lan=zh&ie=UTF-8&spd=1&text=福-->
			<audio id='myAudio' src='https://m10.music.126.net/20181127174645/208892f7508be6f6805be6341ca0d53a/ymusic/4b94/705f/7f83/a7c9d3d74ee10dd36cfdd111e7c171c7.mp3'   controls loop > </audio>
    </div>
</template>
<script>
	export default{
		name:"HomeHeader",
		props:{
			index:Number
		},
		data (){
			return{
				imgAnimate:"",
				title1Animate:"",
				title2Animate:""
			}
		},
		watch:{
			index (){
				if(this.index == 0){
					this.imgAnimate = "imgAnimate"
					this.title1Animate = "title1Animate"
					this.title2Animate = "title2Animate"
				}
				else if(this.index !=0 ){
					this.imgAnimate = ""
					this.title1Animate = ""
					this.title2Animate = ""
				}
			}
		},
		created (){
			this.imgAnimate = "imgAnimate"
			this.title1Animate = "title1Animate"
			this.title2Animate = "title2Animate"
			this.audioCtx = wx.createAudioContext('myAudio')
			this.audioCtx.play();
		},
		
	}
</script>
<style lang="scss" scoped>
	.swiper-header{
	height:100%;
	image{
		height:100%;
		width:100%;
	}
	p{
		position: absolute;
		bottom:-4rem;
		color:white;
		font-size:0.5rem;
		text-shadow:0.1rem 0.2rem 0.4rem #000;
		font-weight: bold;
        padding-left:0.5rem;
        
	}
}
 .imgAnimate{
	animation: imgfade 3s ease 1 forwards;
   -webkit-animation:imgfade 3s ease 1 forwards;
   -o-animation:imgfade 3s ease 1 forwards;
 }
 .title1Animate{
 	animation: move1 1s ease-in-out 2s 1 forwards;
    -webkit-animation: move1 1s ease-in-out 2s 1 forwards;
    -o-animation: move2 1s ease-in-out 2s 1 forwards;
 }
  .title2Animate{
 	animation: move2 1s ease-in-out 2s 1 forwards;
    -webkit-animation:  move2 1s ease-in-out 2s 1 forwards;
    -o-animation: move2 1s ease-in-out 2s 1 forwards;
 }
@keyframes imgfade{
	0%  {opacity: 0 ;}
	40% {opacity: 0.2 ;}
	80% {opacity: 0.8 ;}
	100% {opacity: 1 ;}
}  
@keyframes move1{
	0%{
		bottom:0.2rem;
	}
	
	100%{
		bottom:4rem;
	}
}
@keyframes move2{
	0%{
		bottom:0.2rem;
	}
	
	100%{
		bottom:3rem;
	}
}
</style>