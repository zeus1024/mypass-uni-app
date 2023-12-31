<template>
	<view
		:class="['van-cell', borderClass, centerClass, sizeClass]"
		:hover-class="!disabled && (clickable || isLink) ? 'van-cell--clickable' : ''"
		hover-stay-time="70"
		@click="onClick"
	>
		<view :class="['van-cell__left-icon', icon]" v-if="icon"></view>
		<slot v-else name="icon"></slot>

		<view
			class="van-cell__title"
			:style="[titleWidth ? { flex: `0 0 ${titleWidth}` } : '']"
			v-if="title || label || $slots.title"
			@click="onTitleClick"
		>
			<text v-if="title">{{ title }}</text>
			<slot v-else name="title"></slot>

			<view class="van-cell__label" v-if="label || $slots.label">
				<template v-if="label">
					{{ label }}
				</template>
				<slot v-else name="label"></slot>
			</view>
		</view>

		<view class="van-cell__value" v-if="value">
			<template v-if="value">
				{{ value }}
			</template>
			<slot></slot>
		</view>
		<template v-else><slot></slot></template>

		<view class="van-cell__right-icon van-cell--arrow" v-if="isLink"></view>
		<slot v-else name="right-icon"></slot>

		<slot name="extra"></slot>
	</view>
</template>

<script>
export default {
	name: 'Cell',
	options: {
		multipleSlots: true,
		styleIsolation: 'shared',
		virtualHost: true
	},
	props: {
		title: {
			type: [String, Number],
			default: ''
		},
		value: {
			type: [String, Number],
			default: ''
		},
		label: {
			type: [String, Number],
			default: ''
		},
		url: {
			type: String,
			default: ''
		},
		icon: {
			type: String,
			default: ''
		},
		rightIcon: {
			type: String,
			default: ''
		},
		size: {
			type: String,
			default: ''
		},
		border: {
			type: Boolean,
			default: true
		},
		clickable: {
			type: Boolean,
			default: false
		},
		center: {
			type: Boolean,
			default: false
		},
		isLink: {
			type: Boolean,
			default: false
		},
		titleWidth: {
			type: String,
			default: ''
		},
		linkType: {
			type: String,
			default: 'navigateTo'
		},
		disabled: {
			type: Boolean,
			default: false
		}
	},
	computed: {
		borderClass() {
			return this.border ? '' : 'van-cell--borderless';
		},
		centerClass() {
			return this.center ? 'van-cell--center' : '';
		},
		sizeClass() {
			return this.size === 'large' ? 'van-cell--large' : '';
		}
	},
	methods: {
		onClick(e) {
			if (this.disabled) return;
			this.$emit('click', e);
			this.stop && this.preventEvent(e);

			if (this.linkType == 'navigateTo') {
				uni.navigateTo({
					url: this.url
				});
			} else if (this.linkType == 'switchTab') {
				uni.switchTab({
					url: this.url
				});
			} else if (this.linkType == 'reLaunch') {
				uni.reLaunch({
					url: this.url
				});
			} else if (this.linkType == 'redirectTo') {
				uni.redirectTo({
					url: this.url
				});
			} else {
				uni.navigateTo({
					url: this.url
				});
			}
		},
		onTitleClick(e) {
			if (this.disabled) return;
			this.$emit('title-click', e);
		}
	}
};
</script>

<style lang="scss" src="./style.scss"></style>
