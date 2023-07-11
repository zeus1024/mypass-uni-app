<template>
	<view>
		<uni-list v-for="(item,index) in chatList" :key="index">
			<uni-list-chat :title="item.title"
				:avatar="item.avatar"
				:note="item.note" :time="item.time">
			</uni-list-chat>
		</uni-list>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				chatList: [
					{
						title:'AI项目周天宇',
						avatar:'/static/img/chat/avatar1.jpg',
						note:'知道了',
						time:'11:20'
					},
					{
						title:'后端于成和',
						avatar:'/static/img/chat/avatar4.jpg',
						note:'[图片]',
						time:'11:18'
					},
					{
						title:'百度HR',
						avatar:'/static/img/chat/avatar3.jpg',
						note:'好的，谢谢',
						time:'11:08'
					},
					{
						title:'唐海儿',
						avatar:'/static/img/chat/avatar2.jpg',
						note:'今晚跟你一起睡',
						time:'11:00'
					},
					{
						title:'冯凌萱',
						avatar:'/static/img/chat/avatar5.jpg',
						note:'OK',
						time:'10:50'
					},
					{
						title:'龚虹雨',
						avatar:'/static/img/chat/avatar6.jpg',
						note:'贴贴',
						time:'10:49'
					},
					{
						title:'沈清懿',
						avatar:'/static/img/chat/avatar7.jpg',
						note:'好累啊',
						time:'10:40'
					},
					{
						title:'刘松月',
						avatar:'/static/img/chat/avatar8.jpg',
						note:'复制粘贴',
						time:'10:32'
					},
					{
						title:'冯凌萱',
						avatar:'/static/img/chat/avatar9.jpg',
						note:'CSDN',
						time:'10:21'
					},
					{
						title:'熊曼妮',
						avatar:'/static/img/chat/avatar10.jpg',
						note:'自己不会百度吗',
						time:'10:10'
					},
					{
						title:'冯琳瑜',
						avatar:'/static/img/chat/avatar11.jpg',
						note:'真的是',
						time:'10:01'
					},
					{
						title:'毛惜筠',
						avatar:'/static/img/chat/avatar12.jpg',
						note:'怎么这么多数据',
						time:'09.40'
					},
					{
						title:'江新梅',
						avatar:'/static/img/chat/avatar13.jpg',
						note:'最后一个了',
						time:'09:10'
					},
					
				],

			}
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>

<style>

</style>
