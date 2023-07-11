<template>
	<view>
		<view class="my_img">
			<image class="top" mode="widthFix" src="/static/img/my/my.png"></image>
		</view>
		<uni-list class="topList">
			<uni-list-item showArrow title="服务" thumb="/static/img/my/my1.png">
			</uni-list-item>
		</uni-list>
		<uni-list class="topList">
			<uni-list-item showArrow title="收藏" thumb="/static/img/my/my2.png">
			</uni-list-item>
			<uni-list-item showArrow title="朋友圈" thumb="/static/img/my/my3.png">
			</uni-list-item>
			<uni-list-item showArrow title="卡包" thumb="/static/img/my/my4.png">
			</uni-list-item>
			<uni-list-item showArrow title="表情" thumb="/static/img/my/my5.png">
			</uni-list-item>
		</uni-list>
		<uni-list class="topList">
			<uni-list-item showArrow title="设置" thumb="/static/img/my/my6.png" @click="goToSet()" clickable>
			</uni-list-item>
		</uni-list>
		<uni-popup ref="popup" background-color="#fff">
			<view style="margin-bottom: 80px;">
				<text style="padding: 10px;">请点击<设置>进行配置</text>
			</view>
		</uni-popup>
	</view>
</template>

<script>
	export default {
		data() {
			return {

			}
		},
		mounted() {
			this.$refs.popup.open('bottom')

		},
		methods: {
			goToSet() {
				uni.navigateTo({
					url: '/pages/My/set'
				})
			}
		}
	}
</script>

<style>
	page {
		background-color: rgb(237, 237, 237);
	}

	.my_img {
		width: 100%;
		background-color: white;
		display: flex;
		justify-content: center;

	}

	.top {
		margin-top: 50px;
		margin-left: -10px;
		width: 100%;
	}

	.topList {

		font-size: 16px;
		color: black;
		font-weight: 600;
		margin-top: 8px;


	}
</style>
