<template>
	<view>
		<view>
			<uni-list-item title="消息" thumb="/static/img/scut/xiaoxi.png" thumbSize="lg" class="topList">
			</uni-list-item>
			<uni-list-item title="企业通讯录" thumb="/static/img/scut/qytxl.png" thumbSize="lg" class="topList">
			</uni-list-item>
			<uni-list-item title="我的" thumb="/static/img/scut/my.png" thumbSize="lg" class="topList">
			</uni-list-item>
		</view>
		<view>
			<view class="list-text">
				B
			</view>
			<uni-list-item title="本科教务系统" thumb="/static/img/scut/b1.png" thumbSize="lg" class="topList">
			</uni-list-item>
			<view class="list-text">
				C
			</view>
			<uni-list-item title="财务处" thumb="/static/img/scut/scut.jpg" thumbSize="lg" class="topList">
			</uni-list-item>
			<view class="list-text">
				D
			</view>
			<uni-list-item title="党委宣传部" thumb="/static/img/scut/scut.jpg" thumbSize="lg" class="topList">
			</uni-list-item>
			<uni-list-item title="大学城校区" thumb="/static/img/scut/scut.jpg" thumbSize="lg" class="topList">
			</uni-list-item>
			<view class="list-text">
				E
			</view>
			<uni-list-item title="eduroam" thumb="/static/img/scut/e.jpg" thumbSize="lg" class="topList">
			</uni-list-item>
			<view class="list-text">
				F
			</view>
			<uni-list-item title="分析测试中心" thumb="/static/img/scut/scut.jpg" thumbSize="lg" class="topList">
			</uni-list-item>
			<view class="list-text">
				G
			</view>
			<uni-list-item title="国际校区综合办" thumb="/static/img/scut/scut.jpg" thumbSize="lg" class="topList">
			</uni-list-item>
			<uni-list-item title="智慧后勤" thumb="/static/img/scut/g2.png" thumbSize="lg" class="topList">
			</uni-list-item>
			<view class="list-text">
				H
			</view>
			<uni-list-item title="华工保卫处" thumb="/static/img/scut/h1.jpg" thumbSize="lg" class="topList">
			</uni-list-item>
			<uni-list-item title="会议室预约" thumb="/static/img/scut/scut.jpg" thumbSize="lg" class="topList">
			</uni-list-item>
			<view class="list-text">
				J
			</view>
			<uni-list-item title="纪委办公室、监察处" thumb="/static/img/scut/scut.jpg" thumbSize="lg" class="topList">
			</uni-list-item>
			<view class="list-text">
				K
			</view>
			<uni-list-item title="科学技术研究院" thumb="/static/img/scut/scut.jpg" thumbSize="lg" class="topList">
			</uni-list-item>
			<view class="list-text">
				M
			</view>
			<uni-list-item title="木棉BBS（校园网内试运行）" thumb="/static/img/scut/scut.jpg" thumbSize="lg" class="topList">
			</uni-list-item>
			<uni-list-item title="木棉乐享" thumb="/static/img/scut/m2.png" thumbSize="lg" class="topList">
			</uni-list-item>
			<uni-list-item @click="goToMypass()" clickable title="My Pass 我的通行证" thumb="/static/img/scut/scut.jpg" thumbSize="lg" class="topList">
			</uni-list-item>
			<view class="list-text">
				S
			</view>
			<uni-list-item title="拾卡寻人" thumb="/static/img/scut/s1.png" thumbSize="lg" class="topList">
			</uni-list-item>
			<uni-list-item title="社团OA" thumb="/static/img/scut/s2.jpg" thumbSize="lg" class="topList">
			</uni-list-item>
			<uni-list-item title="师生服务中心" thumb="/static/img/scut/scut.jpg" thumbSize="lg" class="topList">
			</uni-list-item>
			<uni-list-item title="实验室与设备管理处" thumb="/static/img/scut/scut.jpg" thumbSize="lg" class="topList">
			</uni-list-item>
			<view class="list-text">
				T
			</view>
			<uni-list-item title="通知公告" thumb="/static/img/scut/scut.jpg" thumbSize="lg" class="topList">
			</uni-list-item>
			<view class="list-text">
				W
			</view>
			<uni-list-item title="微企通讯录" thumb="/static/img/scut/t1.png" thumbSize="lg" class="topList">
			</uni-list-item>
			<view class="list-text">
				X
			</view>
			<uni-list-item title="消息通知" thumb="/static/img/scut/x1.png" thumbSize="lg" class="topList">
			</uni-list-item>
			<uni-list-item title="校园地图" thumb="/static/img/scut/x2.png" thumbSize="lg" class="topList">
			</uni-list-item>
			<uni-list-item title="校园网" thumb="/static/img/scut/x3.png" thumbSize="lg" class="topList">
			</uni-list-item>
			<uni-list-item title="校园一卡通" thumb="/static/img/scut/x4.jpg" thumbSize="lg" class="topList">
			</uni-list-item>
			<uni-list-item title="学生数据采集" thumb="/static/img/scut/scut.jpg" thumbSize="lg" class="topList">
			</uni-list-item>
			<uni-list-item title="学生资助" thumb="/static/img/scut/scut.jpg" thumbSize="lg" class="topList">
			</uni-list-item>
			<uni-list-item title="虚拟华园" thumb="/static/img/scut/x5.jpg" thumbSize="lg" class="topList">
			</uni-list-item>
			<view class="list-text">
				Y
			</view>
			<uni-list-item title="移动门户" thumb="/static/img/scut/scut.jpg" thumbSize="lg" class="topList">
			</uni-list-item>
			<uni-list-item title="移动图书馆" thumb="/static/img/scut/y2.jpg" thumbSize="lg" class="topList">
			</uni-list-item>
			<uni-list-item title="医疗器械检验研究中心" thumb="/static/img/scut/scut.jpg" thumbSize="lg" class="topList">
			</uni-list-item>
			<uni-list-item title="疫情防控专区" thumb="/static/img/scut/y3.jpg" thumbSize="lg" class="topList">
			</uni-list-item>
			<uni-list-item title="一张表" thumb="/static/img/scut/y4.jpg" thumbSize="lg" class="topList">
			</uni-list-item>
		</view>
	</view>
</template>

<script>
	export default{
		data(){
			return{
				
			}
		},
		methods:{
			goToMypass(){
				uni.navigateTo({
					url: '/pages/Scut/Mypass/index'
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
	.list-text {
		color: gray;
		font-size: 12px;
		padding: 4px 2px 4px  8px;
		padding-left: 16px;
		background-color: #efefef;
	}
</style>