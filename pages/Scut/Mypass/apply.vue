<!-- 外出申请页面 -->
<template>
	<view id="apply">
		<uni-nav-bar :fixed="true" left-icon="closeempty" right-icon="more-filled" title="外出申请" color="#000"
			@clickLeft="goBack()" status-bar backgroundColor="#efefef"/>


		<view>
			<view class="greyText">申请流程</view>
			<view class="applyProcess rowBox">
				<view class="rowBox">
					<image class="applyProcess_img" src="../../../static/img/mypass/true.png"></image>
					<p>提交</p>
					<span>——</span>

				</view>
				<view class="rowBox">
					<image class="applyProcess_img" src="../../../static/img/mypass/true.png"></image>
					<p>院级审批</p>
					<span>——</span>
				</view>
				<view class="rowBox">
					<image class="applyProcess_img" src="../../../static/img/mypass/true.png"></image>
					<p>校级审批</p>
				</view>
			</view>

		</view>
		<view>
			<view class="greyText">外出信息</view>
			<!-- 开始日期 -->
			<uni-list>
				<uni-list-item>
					<!-- 自定义 header -->
					<template v-slot:header>
						<span class="bt">*</span>
					</template>
					<!-- 自定义 body -->
					<template v-slot:body>
						<text class="custom-title slot-box slot-text">开始日期</text>
					</template>
					<!-- 自定义 footer-->
					<template v-slot:footer>
						<text class="valueText">{{msg.startDate}}</text>
						<span class="choose-text">选择</span>
					</template>
				</uni-list-item>
			</uni-list>


			<!-- 结束日期 -->
			<uni-list>
				<uni-list-item>
					<!-- 自定义 header -->
					<template v-slot:header>
						<span class="bt">*</span>
					</template>
					<!-- 自定义 body -->
					<template v-slot:body>
						<text class="custom-title slot-box slot-text">结束日期</text>
					</template>
					<!-- 自定义 footer-->
					<template v-slot:footer>
						<text class="valueText">{{msg.endDate}}</text>
						<span class="choose-text">选择</span>
					</template>
				</uni-list-item>
			</uni-list>
			<!-- 外出地点 -->
			<uni-list>
				<uni-list-item>
					<!-- 自定义 header -->
					<template v-slot:header>
						<span class="bt">*</span>
					</template>
					<!-- 自定义 body -->
					<template v-slot:body>
						<text class="custom-title slot-box slot-text ">外出地点</text>
					</template>
					<!-- 自定义 footer-->
					<template v-slot:footer>
						<text class="valueText "
							style="width:180px;white-space: nowrap;direction:rtl;overflow: hidden;">{{msg.place}}</text>
					</template>
				</uni-list-item>
			</uni-list>

			<!-- 外出事由 -->

			<uni-section style="font-size: 14px;" title="外出事由" padding>
				<template v-slot:decoration>
					<span class="bt" style="margin-left:4px;margin-right: 6px;">*</span>
				</template>
					<text class="reason_text">{{msg.reason}}</text>
			</uni-section>

		</view>
		<view>
			<view class="greyText">我的信息</view>
			<view>
				<uni-list-item>
					<!-- 自定义 body -->
					<template v-slot:body>
						<text class=" slot-box slot-text msg_text">姓名</text>
					</template>
					<!-- 自定义 footer-->
					<template v-slot:footer>
						<text class="msg_text">{{student.name}}</text>
					</template>
				</uni-list-item>
			</view>
			<view>
				<uni-list-item>
					<!-- 自定义 body -->
					<template v-slot:body>
						<text class=" slot-box slot-text msg_text">学号</text>
					</template>
					<!-- 自定义 footer-->
					<template v-slot:footer>
						<text class="msg_text">{{student.id}}</text>
					</template>
				</uni-list-item>
			</view>
			<view>
				<uni-list-item>
					<!-- 自定义 body -->
					<template v-slot:body>
						<text class=" slot-box slot-text msg_text">学院</text>
					</template>
					<!-- 自定义 footer-->
					<template v-slot:footer>
						<text class="msg_text">{{student.college}}</text>
					</template>
				</uni-list-item>
			</view>
			<view>
				<uni-list-item>
					<!-- 自定义 body -->
					<template v-slot:body>
						<text class=" slot-box slot-text msg_text">年级</text>
					</template>
					<!-- 自定义 footer-->
					<template v-slot:footer>
						<text class="msg_text">{{student.grade}}</text>
					</template>
				</uni-list-item>
			</view>
			<view>
				<uni-list-item>
					<!-- 自定义 body -->
					<template v-slot:body>
						<text class=" slot-box slot-text msg_text">类型</text>
					</template>
					<!-- 自定义 footer-->
					<template v-slot:footer>
						<text class="msg_text">{{student.type}}</text>
					</template>
				</uni-list-item>
			</view>
		</view>
		<view>
			<view class="greyText">
				温馨提示：每次只能发起一次外出申请，外出申请生效期间内无法再次发起申请。
			</view>
			<view style="height:30px;background-color: white;"></view>
		</view>
		<!-- 已批准 -->
		<view>
			<image class="pass" src="../../../static/img/mypass/pass.png"></image>
		</view>
		<view>

		</view>
	</view>
</template>

<script>

	export default {
		name: 'apply',
		data() {
			return {
				msg: {
					startDate: new Date().toISOString().slice(0, 10),
					endDate: new Date().toISOString().slice(0, 10),
					place: '天河区中山三院',
					reason: '去医院看胃病',
				},

				student: {
					name: '张三',
					id: '202003143104',
					college: '土木与交通学院',
					grade: '2020级',
					type: '本科生'
				}
			}
		},
		created() {
			const msg = uni.getStorageSync('msg');
			const student = uni.getStorageSync('student')
			if (msg) {
				this.msg = msg
			}
			if (student) {
				this.student = student
			}
		},
		methods: {
			noBomBox(Event) {
				if (!this.isinput) {
					document.activeElement.blur();
				}
			},
			goBack() {
				// uni.redirectTo({
				// 	url: '/pages/Scut/index'
				// })
				uni.navigateBack()
			}
		},

	}
</script>

<style>
	#apply {
		background-color: #eeeeee;
		height: 100%;
	}

	.greyText {
		color: gray;
		padding: 12px;
		font-size: 14px;
	}

	.applyProcess {
		background-color: #fff;
		padding: 16px;
	}

	.rowBox {
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: center;
	}

	.applyProcess_img {
		width: 21px;
		height: 21px;
		margin: 0 5.2px;
		position: relative;
	}

	.applyProcess p {
		display: inline-block;
		color: #7f7f7f;

		margin: 0;
		padding: 0;
	}

	.applyProcess span {
		color: #7f7f7f;
		margin: 0.1rem;
	}

	.bt {
		color: red;
		font-weight: 700;
		margin-right: 5px;
	}

	.custom-title {
		font-size: 14px;
		font-weight: 400;
		opacity: 0.85;
	}

	.choose-text {
		font-size: 14px;
		color: #2095FE;
		margin-left: 8px;
	}

	.valueText {
		color: #191919;
		font-size: 14px;
	}


	.labelText {
		color: black;
		margin-right: 100px;
	}

	.pass {
		position: fixed;
		top: 15%;
		left: 5%;
		
		z-index: 10;
	}

	.slot-box {
		/* #ifndef APP-NVUE */
		display: flex;
		/* #endif */
		flex-direction: row;
		align-items: center;
	}

	.slot-text {
		flex: 1;
		font-size: 14px;
		margin-right: 10px;
	}

	.msg_text {
		font-size: 15px;
		color: rgb(51, 51, 51);
	}
	.reason_text{
		display: block;
		width: 100%;
		height: 50px;
		border: #efefef 1.5px solid;
		padding: 8px;
		font-size: 14px;
		color: #191919;
	}
</style>
