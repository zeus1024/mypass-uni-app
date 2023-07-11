<template>
	<view id="bg">
		<uni-nav-bar :fixed="true" left-icon="closeempty" right-icon="more-filled" title="首页" color="#000"
			@clickLeft="goBack()" status-bar backgroundColor="#efefef" />

		<view class="main">
			<view class="main_box">
				<view class="main_title">
					<image class="main_title_img" src="/static/img/mypass/title_left.png"></image>
					<text>采集</text>
					<image class="main_title_img" src="/static/img/mypass/title_right.png"></image>
				</view>
				<view class="main_section">
					<view class="item">
						<image class="item_icon" src="../../../static/img/mypass/a1.png"></image>
						<view class="text">人脸采集</view>
					</view>
					<view class="item">
						<image class="item_icon" src="../../../static/img/mypass/a2.png"></image>
						<view class="text">使用授权</view>
					</view>
				</view>
			</view>
			<view class="main_box">
				<view class="main_title">
					<image class="main_title_img" src="/static/img/mypass/title_left.png"></image>
					<text>在校</text>
					<image class="main_title_img" src="/static/img/mypass/title_right.png"></image>
				</view>
				<view class="main_section">
					<view class="item" @click="goToApply()">
						<image class="item_icon" src="../../../static/img/mypass/b1.png"></image>
						<view class="text">外出申请</view>
					</view>
				</view>
			</view>
			<view class="main_box">
				<view class="main_title">
					<image class="main_title_img" src="/static/img/mypass/title_left.png"></image>

					<text>离校·返校</text>
					<image class="main_title_img" src="/static/img/mypass/title_right.png"></image>
				</view>
				<view class="main_section">
					<view class="item">
						<image class="item_icon" src="../../../static/img/mypass/c1.png"></image>
						<view class="text">离校登记</view>
					</view>
					<view class="item">
						<image class="item_icon" src="../../../static/img/mypass/c2.png"></image>
						<view class="text">返校申请</view>
					</view>
					<view class="item">
						<image class="item_icon" src="../../../static/img/mypass/c3.png"></image>
						<view class="text">返程填报</view>
					</view>
				</view>
			</view>
			<view class="main_box">
				<view class="main_title">
					<image class="main_title_img" src="/static/img/mypass/title_left.png"></image> <text>报到</text>
					<image class="main_title_img" src="/static/img/mypass/title_right.png"></image>
				</view>
				<view class="main_section">
					<view class="item">
						<image class="item_icon" src="../../../static/img/mypass/d1.png"></image>
						<view class="text">开学报到</view>
					</view>
				</view>
			</view>
			<view class="main_box">
				<view class="main_title">
					<image class="main_title_img" src="/static/img/mypass/title_left.png"></image>
					<text>健康信息</text>
					<image class="main_title_img" src="/static/img/mypass/title_left.png"></image>
				</view>
				<view class="main_section">
					<view class="item">
						<image class="item_icon" src="../../../static/img/mypass/e1.png"></image>
						<view class="text">健康填报</view>
					</view>
					<view class="item">
						<image class="item_icon" src="../../../static/img/mypass/e2.png"></image>
						<view class="text">排查登记</view>
					</view>
				</view>
			</view>
			<view>
				<button class="back_btn" type="primary">退出登录</button>

			</view>
		</view>

		<view id="footer">
			<text>粤ICP备05084312号</text>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {

			}
		},
		methods: {
			goToApply() {
				uni.redirectTo({
					url: '/pages/Scut/Mypass/apply'
				})
			},
			goBack() {
				uni.navigateBack()
				// uni.redirectTo({
				// 	url:'/pages/Scut/index'
				// })
			}
		}
	}
</script>

<style>
	#bg {
		background: #EDF1F5 url('/static/img/mypass/bg.png') no-repeat;
		background-size: 100% 300px;
		height: 95vh;
		box-sizing: border-box;
		overflow-y: hidden;
	}

	.main {
		height: 86%;
		width: 90%;
		position: fixed;
		left: 5%;
		margin-top: 14px;
		box-sizing: border-box;
		overflow-y: scroll;
	}


	.main_box {
		width: 100%;
		border-radius: 20px;
		background-color: #fff;
		box-sizing: border-box;
		padding: 20px;
		margin-bottom: 12px;
	}

	.main_title {
		display: flex;
		justify-content: center;
		align-items: center;
		color: #181a1a;
		font-size: 18px;
		font-weight: 700;
		padding-bottom: 10rpx;
	}

	.main_title_img {
		height: 12px;
		width: 20px;
		margin: 5px;
	}

	.main_section {
		display: flex;
		flex-wrap: wrap;
	}

	.item {
		width: 33%;
		display: flex;
		flex-direction: column;
		align-items: center;
		margin-top: 22px;
		position: relative;
	}

	.item .item_icon {
		
		height: 48px;
		width: 48px;
	}

	.item>.text {
		width: 100%;
		text-align: center;
		margin-top: 8px;
		font-size: 14px;
		font-weight: 700;
		color: #051e33;
	}

	.back_btn {
		width: 100%;
		text-align: center;
		box-sizing: border-box;
		background-color: #48a0fa;
		color: #fff;
		border-radius: 10px;
		margin: 0 auto;
		font-size: 14px;
		margin-top: .3rem;
		margin-bottom: 20px;
	}

	#footer {
		position: fixed;
		height: 5%;
		bottom: 0px;
		width: 100%;
		text-align: center;
		color: #999;
		background-color: #edf1f5;
	}
</style>
