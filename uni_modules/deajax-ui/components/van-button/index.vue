<template>
	<button
		:id="id"
		data-detail="dataset"
		:class="[
			'van-button',
			`van-button--${type}`,
			`van-button--${size}`,
			block ? 'van-button--block' : '',
			round ? 'van-button--round' : '',
			plain ? 'van-button--plain' : '',
			square ? 'van-button--square' : '',
			loading ? 'van-button--loading' : '',
			disabled ? 'van-button--disabled' : '',
			hairline ? 'van-button--hairline' : ''
		]"
		:hover-class="disabled || loading ? '' : 'van-button--active hover-class'"
		:lang="lang"
		:form-type="formType"
		:style="[color && !plain ? colorStyle : color && plain ? plainColorStyle : '', customStyle]"
		:open-type="[
			disabled || loading || (canIUseGetUserProfile && openType === 'getUserInfo')
				? ''
				: openType
		]"
		:business-id="businessId"
		:session-from="sessionFrom"
		:sendMessagetitle="sendMessageTitle"
		:sendMessagepath="sendMessagePath"
		:sendMessageimg="sendMessageImg"
		:showMessagecard="showMessageCard"
		:app-parameter="appParameter"
		:aria-label="ariaLabel"
		@click="onClick"
		@getuserinfo="onGetUserInfo"
		@contact="onContact"
		@getphonenumber="onGetPhoneNumber"
		@error="onError"
		@launchapp="onLaunchApp"
		@opensetting="onOpenSetting"
	>
		<template v-if="loading">
			<view :class="['van-button__loading']" :style="[loadingFont]">
				<view
					:class="[
						loadingType == 'circular'
							? 'ri-loader-4-line'
							: loadingType == 'spinner'
							? 'ri-loader-2-line'
							: 'ri-loader-4-line'
					]"
				/>
			</view>
			<view v-if="loadingText" class="van-button__loading-text">{{ loadingText }}</view>
		</template>
		<template v-else>
			<view v-if="icon" :class="['van-button__icon', icon]"></view>
			<view class="van-button__text"><slot /></view>
		</template>
	</button>
</template>

<script>
export default {
	name: 'Button',
	options: {
		multipleSlots: true,
		styleIsolation: 'shared',
		virtualHost: true
	},
	props: {
		type: {
			type: String,
			default: 'default'
		},
		size: {
			type: String,
			default: 'normal'
		},
		color: String,
		icon: String,
		plain: Boolean,
		block: Boolean,
		round: Boolean,
		square: Boolean,
		disabled: Boolean,
		hairline: Boolean,
		loading: Boolean,
		loadingText: String,
		loadingType: {
			type: String,
			default: 'circular'
		},
		loadingSize: {
			type: String,
			default: '20px'
		},
		customStyle: String,
		openType: String,
		appParameter: String,
		lang: {
			type: String,
			default: 'en'
		},
		sessionFrom: String,
		businessId: Number,
		sendMessageTitle: String,
		sendMessagePath: String,
		sendMessageImg: String,
		showMessageCard: String,
		dataset: null,
		formType: String
	},
	data() {
		return {
			loadingColor: ''
		};
	},
	computed: {
		colorStyle() {
			return {
				color: 'white',
				background: `${this.color}`,
				border: 'none'
			};
		},
		plainColorStyle() {
			return {
				color: `${this.color}`,
				borderColor: `${this.color}`
			};
		},
		loadingFont() {
			return {
				fontSize: `${this.loadingSize}`
			};
		}
	},
	methods: {
		onClick(e) {
			this.$emit('click', e);
			this.stop && this.preventEvent(e);
		},
		onGetUserInfo(e) {
			this.$emit('getuserinfo', e);
		},
		onContact(e) {
			this.$emit('contact', e);
		},
		onGetPhoneNumber(e) {
			this.$emit('getphonenumber', e);
		},
		onError(e) {
			this.$emit('error', e);
		},
		onLaunchApp(e) {
			this.$emit('launchapp', e);
		},
		onOpenSetting(e) {
			this.$emit('opensetting', e);
		}
	}
};
</script>

<style lang="scss" src="./style.scss"></style>
