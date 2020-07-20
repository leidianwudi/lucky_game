<template>
	<view class="content">
		<!-- 背景图片 -->
		<image src="/static/img/6764fbf06a78763f6b2162e6d4bd731c.png" mode="" class="bg-set"></image>
		<!-- 左上更多图标 -->
		<view class="gz">
			<image src="/static/img/gz.c859c3e0.png" mode="widthFix"></image>
		</view>
		<!-- 右上奖品图标 -->
		<view class="jp">
			<image src="/static/img/jp.f4cc450a.png" mode="widthFix"></image>
		</view>
		<!-- 顶部文字 -->
		<view class="active_test">
			福建省用户专享活动
		</view>
		<!-- 红包领奖进度条 -->
		<view class="list">
			<!-- 外部进度条 -->
			<view class="botline"> 
				<!-- 内部进度条 -->
				<view class="topline" :style="{width:width + '%'}"></view>
			</view>
			<!-- 奖励红包 -->
			<view class="progress_award">
				<image src="/static/img/2baa8604a9b148c7451de22336a6557e.png" mode="widthFix"></image>
			</view>
			<view class="progress_award awardT">
				<image src="/static/img/2baa8604a9b148c7451de22336a6557e.png" mode="widthFix"></image>
			</view>
			<view class="progress_award awardS">
				<image src="/static/img/2baa8604a9b148c7451de22336a6557e.png" mode="widthFix"></image>
			</view>
			<view class="">
				<view class="progress_award awardF">
					<image src="/static/img/3584f21da8adbe692696a04e1633d966.png" mode="widthFix"></image>
				</view>
				<view class="award_test">可以提现的哦!<text></text></view>
			</view>
		</view>
		
		<!-- 转盘 -->
		<view class="luckdraw_box">
			<view class="rotate">
				<image src="/static/img/58ea510e1129b8b4287e32e2f3b064ed.png" mode="widthFix"></image>
				<view class="award award_r">
					<text>任天堂游戏机</text>
					<view class="award_img">
						<image src="/static/img/6a823b1a9f4b244436e9e7376b049edc.png" mode=""></image>
					</view>
				</view>
				
				<view class="award award_p">
					<text>苹果手机</text>
					<view class="award_img">
						<image src="/static/img/e406717b3f419326668850fb2e97b65b.png" mode=""></image>
					</view>
				</view>
				
				<view class="award award_j">
					<text>黄金</text>
					<view class="award_img">
						<image src="/static/img/a08a2e7a9002de1284345492b07e2678.png" mode=""></image>
					</view>
				</view>
				
				<view class="award award_h">
					<text>200元红包</text>
					<view class="award_img">
						<image src="/static/img/6a6e30c4b997f653404f956d00660200.png" mode=""></image>
					</view>
				</view>
				
				<view class="award award_x">
					<text>幸运奖</text>
					<view class="award_img">
						<image src="/static/img/6b409b67de90070099dfbf74556f12bc.png" mode=""></image>
					</view>
				</view>
				
				<view class="award award_s">
					<text>谢谢参与</text>
					<view class="award_img">
						<image src="/static/img/b3f549df59ac0c05fa3894f6adef9c11.png" mode=""></image>
					</view>
				</view>
			</view>
			<view class="luck_draw">
				<image src="/static/img/lamp1.40547699.png" mode="widthFix" v-show="effect"></image>
				<image src="/static/img/lamp2.062c14d4.png" mode="widthFix" v-show="!effect"></image>
			</view>
			<view class="pointer" @click="openLucky">
				<image src="/static/img/ef5b234566bdb5d9f3d261c814fe44b0.png" mode=""></image>
			</view>
		</view>
		
		
		
		
		
		<!-- 遮罩层 -->
		<view class="shadow" v-show="shadow">
			<view class="main" @tap="openUrl">
				<!-- 领奖标题头图片 -->
				<view class="card card_header">
					<image src="/static/img/lotteryend3.95b0b826.png" mode="widthFix"></image>
				</view>
				<!-- 遮罩层背景 -->
				<view class="card card_content1">
					<image src="/static/img/lotteryend2.ba11eeb8.png" mode=""></image>
				</view>
			
				<!-- 遮罩层活动 -->
				<view class="active1">
					<!-- 活动背景图 -->
					<image src="/static/img/lotteryend2.ba11eeb8.png" mode=""></image>
					<!-- 活动内容 -->
					<view class="active1_img">
					</view>
				</view>
				
				<view class="close" @click.stop="close">
					<image src="/static/img/close.png" mode=""></image>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
import config from "@/static/config/config.js"
	export default {
		data() {
			return {
				width: 28, 		//进度条长度
				effect: true,   //转盘外部动画控制
				shadow: false,  //遮罩层
			}
		},
		onLoad() {
			this.openEffectAnimation();  //打开转盘外部动画
		},
		methods: {
			//打开转盘外部动画
			openEffectAnimation(){
				setInterval(this.effectAnimation, 1000);
			},
			//转盘外部动画
			effectAnimation(){
				this.effect  = this.effect ? false : true;
			},
			//打开外部网站
			openUrl(){
				 location.href = config.baseUrl;
			},
			//开启抽奖
			openLucky(){
				this.shadow = true;
			},
			//关闭遮罩层
			close(){
				this.shadow = false;
			},
		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}
	.bg-set, .shadow{
	    position: fixed;
	    width: 100%;
	    height: 100%;
	    top: 0;
	    left: 0;
	    z-index: -1;
	}
	.gz, .jp{
		width:90rpx;
		height:90rpx;
		position: absolute;
	}
	.gz{
		left: 10rpx;
		top: 10rpx;
	}
	.jp{
		right: 10rpx;
		top: 10rpx;
	}
	.active_test{
		color:#ffdf81;
		position:absolute;
		top:15%;
		font-size:17px;
	}
	.list{
		position:absolute;
		top:320rpx;
		z-index:5;
	}
	.botline{
		width:500rpx;
		height:20rpx;
		border-radius:10rpx;
		border:1px solid #fff3dd;
		background-color:rgba(255, 217, 147 ,.6);
	}
	.topline{
		height:20rpx;
		background-color:#91dc0d;
		border-radius:10rpx;
	}
	.progress_award{
		width:70rpx;
		height:80rpx;
		position: absolute;
		transform:translateY(-60%);
		left:10%;
	}
	.awardT{
		left:30%;
	}
	.awardS{
		left:50%;
	}
	.awardF{
		top:7rpx;
		left:83%;
	}
	.award_test{
		width:160rpx;
		height:34rpx;
		background-color:#fe5644;
		font-size:12px;
		color:#fedcac;
		border-radius:10rpx;
		padding:0 10rpx;
		position:absolute;
		right: -40rpx;
		top:60rpx;
	}
	.award_test>text{
		width:0rpx;
		height:0rpx;
		border-top:10rpx solid transparent;
		border-bottom:10rpx solid #ff4007;
		border-right:10rpx solid transparent;
		border-left:10rpx solid transparent;
		display:inline-block;
		position:absolute;
		left:45%;
		top:-16rpx;
	}
	.luckdraw_box{
		width:750rpx;
		height:750rpx;
		position:absolute;
		bottom:200rpx;
	}
	.rotate{
		width:750rpx;
		height:750rpx;
		position:absolute;
		top:0;
		left:0;
		animation:rotate  8s linear infinite;
		transform-origin:center;/*定义bai动画的旋转中心点*/
		z-index: 3;
	}
	@keyframes rotate {
		0%{transform:rotate(0deg);}
		25%{transform:rotate(90deg);}
		50%{transform:rotate(180deg);}
		75%{transform:rotate(270deg);}
		100%{transform:rotate(360deg);}
	}
	.luck_draw{
		width:740rpx;
		height:700rpx;
		position:absolute;
		transform: translateY(0);
		z-index:4;
	}
	.pointer{
		width:280rpx;
		height:300rpx;
		position:absolute;
		top:50%;
		left:50%;
		z-index: 10;
		transform: translate(-50%, -50%);
		animation: spin 1s infinite;
		transform-origin: 0 0;
	}
	@keyframes spin {	  
	  0%   {
	  	transform:scale(1.2) translate(-50%, -50%);
	  }
	  25%   {
	  	transform:scale(1) translate(-50%, -50%);
	  }
	  50%   {
	  	transform:scale(1.2) translate(-50%, -50%);
	  }
	  75%   {
		transform:scale(1) translate(-50%, -50%);
	  }
	  100%   {
		transform:scale(1.2) translate(-50%, -50%);
	  }
	}
	.award{
		text-align:center;
		color:#ff9e23;
		font-size:16px;
		position:absolute;
	}
	.award_img{
		margin:auto;
		width:120rpx;
		height:120rpx;
	}
	.award_r{
		top:10%;
		left:37%;
	}
	.award_p{
		top:28%;
		left:68%;
		transform:rotate(70deg);
	}
	.award_j{
		top:55%;
		left:67%;
		transform:rotate(120deg);
	}
	.award_h{
		top:67%;
		left:40%;
		transform:rotate(180deg);
	}
	.award_x{
		top:54%;
		left:18%;
		transform:rotate(240deg);
	}
	.award_s{
		top:25%;
		left:16%;
		transform:rotate(300deg);
	}
	
	
	/* 遮罩层 */
	.shadow{
		z-index:999;
		background-color:rgba(50, 37, 15, .7);
	}
	.card{
		width:86%;
		height:400rpx;
		position:absolute;
		left:50%;
	}
	.card_header{
		width:668rpx;
		top:620rpx;
		transform: translate(-50%, -50%);
		z-index:10;
	}
	.card_content1{
		width:630rpx;
		top:900rpx;
		transform: translate(-50%, -50%);
	}
	.active1{
		width:720rpx;
		height:380rpx;
		position:absolute;
		left:50%;
		top:800rpx;
		z-index: 10;
		transform: translate(-50%, -50%);
		background-image: url(/static/img/lotteryend2.ba11eeb8.png) repeat;
		background-size:100% 100%;
	}
	.active1_img{
		position:absolute;
		width:700rpx;
		height:320rpx;
		top:50%;
		left:50%;
		background-image: url(/static/config/active.jpg);
		transform: translate(-50%, -50%);
		border-radius:10rpx;
		background-size:100% 100%;
	}
	.active1_img>image{
		width:100%;
		height:auto;
	}
	.active1_btn{
		width:300rpx;
		height:140rpx;
		position:absolute;
		left:50%;
		transform: translate(-50%, -40%);
	}
	.close{
		width:80rpx;
		height:80rpx;
		position:absolute;
		top:1120rpx;
		left:50%;
		transform: translateX(-50%);
	}
</style>
