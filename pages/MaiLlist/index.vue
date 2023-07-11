<template>
	<view>
		<uni-list v-for="(item,index) in topList" :key="index">
			<uni-list-item :title="item.title" :thumb="item.thumb" thumbSize="lg" class="topList">
			</uni-list-item>
		</uni-list>
		<view class="business-text">
			<text>我的企业及企业联系人</text>
		</view>
		<uni-list-item title="企业微信联系人" thumb="/static/img/mailList/business.png" thumbSize="lg" class="topList">
		</uni-list-item>
		<uni-list-item title="华南理工大学" thumb="/static/img/mailList/scut.jpg" thumbSize="lg" class="topList"
			@click="openScut()" clickable>
		</uni-list-item>
		<view class="list-text">
			A
		</view>
		<uni-list-item title="AI项目周天宇" thumb="/static/img/chat/avatar1.jpg" thumbSize="lg" class="topList">
		</uni-list-item>
		<view class="list-text">
			B
		</view>
		<uni-list-item title="百度HR" thumb="/static/img/chat/avatar3.jpg" thumbSize="lg" class="topList">
		</uni-list-item>
		<uni-list-item title="贝贝" thumb="/static/img/chat/avatar9.jpg" thumbSize="lg" class="topList">
		</uni-list-item>
		<view class="list-text">
			C
		</view>
		<uni-list-item title="陈杰舟" thumb="/static/img/chat/avatar4.jpg" thumbSize="lg" class="topList">
		</uni-list-item>
		<uni-list-item title="陈原" thumb="/static/img/chat/avatar5.jpg" thumbSize="lg" class="topList">
		</uni-list-item>
		<uni-list-item title="陈一鸣" thumb="/static/img/chat/avatar2.jpg" thumbSize="lg" class="topList">
		</uni-list-item>
		<uni-list-item title="陈洲" thumb="/static/img/chat/avatar7.jpg" thumbSize="lg" class="topList">
		</uni-list-item>
		<view class="list-text">
			D
		</view>
		<uni-list-item title="邓元" thumb="/static/img/chat/avatar7.jpg" thumbSize="lg" class="topList">
		</uni-list-item>
		<uni-list-item title="邓紫棋" thumb="/static/img/chat/avatar10.jpg" thumbSize="lg" class="topList">
		</uni-list-item>
		<uni-list-item title="邓龙" thumb="/static/img/chat/avatar12.jpg" thumbSize="lg" class="topList">
		</uni-list-item>
		<uni-list-item title="邓洲" thumb="/static/img/chat/avatar8.jpg" thumbSize="lg" class="topList">
		</uni-list-item>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				topList: [{
						title: '新的朋友',
						thumb: '/static/img/mailList/newFriend.png',
					},
					{
						title: '仅聊天的朋友',
						thumb: '/static/img/mailList/justChat.png',
					},
					{
						title: '群聊',
						thumb: '/static/img/mailList/chats.png',
					},
					{
						title: '标签',
						thumb: '/static/img/mailList/tags.png',
					},
					{
						title: '公众号',
						thumb: '/static/img/mailList/gzh.png',
					},
				]

			}
		},
		onLoad() {

		},
		methods: {
			openScut() {
				uni.navigateTo({
					url: '/pages/Scut/index',
				});
			}
		}
	}
</script>

<style>
	.topList {
		font-size: 16px;
		color: black;
		font-weight: 600;
	}

	.business-text {
		color: gray;
		font-size: 12px;
		padding: 8px;
		padding-left: 16px;
		background-color: #efefef;
	}

	.list-text {
		color: gray;
		font-size: 12px;
		padding: 8px;
		padding-left: 16px;
		background-color: #efefef;
	}
</style>
