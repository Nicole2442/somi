<template>
	<view class="all">
		<uniPopup type="top" ref="popup">
			<view class="popupview">
				<button class="btn_pop">sss</button>
			</view>
		</uniPopup>
		<view class="userinforbar">
			<image class="logo" src="/static/user.png"></image>
			<text class="username">{{username}}</text>
		</view>
		<view>
			<view class="line"></view>
			<scroll-view class="tabbar" scroll-x="true" >
				<block v-for="(item,index) in tabBars" :key="index">
					<view class="tabbar-items" :class="{'active': tabIndex==index}" @tap="toggleTab(index)">
						{{item.name}}
					</view>
				</block>
			</scroll-view>
			<view class="content">
				<swiper :current="tabIndex" @change="tabChange">
					<swiper-item v-for="(a,index) in contentList" :key="index">
						<text>{{a}}</text>
					</swiper-item>
				</swiper>
			</view>
		</view>
		
	</view>
</template>
<script>
	import uniPopup from'@/components/uni-popup/uni-popup.vue'
	export default {
		components:{uniPopup},
		data() {
			return {
				num:0,
				tabIndex:0,
				timerid:0,
				username: '秦鹭云',
				contentList: [
					"秦鹭云\n男\nbsl\n极其健康",
					"无",
					"基线值"
							],
				tabBars:[
					{
						name: '基本信息',
						id: 'information'
					},
					{
						name: '疾病药物史',
						id: 'drughistroy'
					},
					{
						name: '基线值',
						id: 'baseline'
					}
						]
			}
		},
		onLoad() {
			uni.setStorage({
				key:'test',
				data:'qqq',
				success() {
					console.log('持久了');
				}
			}),
			this.timerid = setInterval(()=>{
				this.num += 1,
				console.log('qqq'+ this.num)
			},2000),
			console.log(this.timerid + 'ID')
			uni.$once('close',()=>{
				console.log('触发了');
				clearInterval(this.timerid)
			})
		},
		onNavigationBarButtonTap(e) {
			if (e.index == 0){
				uni.reLaunch({
					url:'../backservicetest/backservicetest'
				})
				//this.$refs.popup.open()
			}
		},
		methods: {
			//切换选项卡
			toggleTab (index) { 
				this.tabIndex=index;
				console.log(index)
			},
			tabChange(e){
				this.tabIndex = e.detail.current
			}
		}
	}
</script>

<style>
	.popupview{
		width: 60%;
		margin-left: 0px;
	}
	.all{
		flex-direction: column;
	}
	.userinforbar {
		display: flex;
		flex-direction:row;
		align-items: center;
		justify-content: center;
	}
	.content{
		margin-left: 40rpx;
	}
	.line{
		width: 94%;
		margin-left: 3%;
		margin-bottom: 8rpx;
		height: 1rpx;
		border-top: solid #333333 1rpx;
	}
	.tabbar{
		white-space: nowrap;
		border-bottom: #999999 1rpx solid;
	}
	.tabbar .active{
		background-color: #999999;
	}
	.tabbar-items{
		display: inline-block;
		margin: 20rpx 30rpx 30rpx;
		font-size: small;
	}
	.logo {
		height: 200rpx;
		width: 200rpx;
		border-radius: 50%;
		margin-top: 20rpx;
		margin-left: 100rpx;
		margin-bottom: 50rpx;
	}
	.text-area {
		display: flex;
		justify-content: center;
	}
	.username {
		font-size: 36rpx;
		color: #8f8f94;
		align-items: center;
		margin-right: auto;
		margin-left: 20rpx;
	}
</style>
