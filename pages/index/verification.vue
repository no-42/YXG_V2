<template>
	<view class="wrap">
		<u-toast ref="uToast"></u-toast>
		<u-code :seconds="seconds" @end="end" @start="start" ref="uCode" @change="codeChange"></u-code>
		<u-code-input :maxlength="4" v-model="code" mode="line" @finish="finish"></u-code-input>
		<u-button class="verification-button-text" :disabled="buttonDisabled" @tap="getCode">{{tips}}</u-button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				tips: '',
				seconds: 60,
				buttonDisabled: false,
				code: '',
				register: {
					
				}
			}
		},
		onLoad(option) {
			console.log(option);
			this.register = option;
		},
		onReady() {
			// 注意这里不能将一个组件赋值给data的一个变量，否则在微信小程序会
			// 造成循环引用而报错，如果你想这样做，请在非data中定义refCode变量
			// this.refCode = this.$refs.uCode;
		},
		methods: {
			codeChange(text) {
				this.tips = text;
			},
			getCode() {
				if (this.$refs.uCode.canGetCode) {
					// 模拟向后端请求验证码
					uni.showLoading({
						title: '正在获取验证码'
					})
					setTimeout(() => {
						this.buttonDisabled = true
						uni.hideLoading();
						// 这里此提示会被this.start()方法中的提示覆盖
						uni.$u.toast('验证码已发送');
						// 通知验证码组件内部开始倒计时
						this.$refs.uCode.start();
					}, 2000);
				}
				/* else {
					uni.$u.toast('倒计时结束后再发送');
				} */
			},
			end() {
				this.buttonDisabled = false;
				// uni.$u.toast('倒计时结束');
			},
			start() {
				// uni.$u.toast('倒计时开始');
			},
			finish() {
				console.log(this.register);
				console.log(this.code);
				uni.redirectTo({
					url:"/pages/index/userMain?signName=" + this.register.sign
				})
			}
		}
	}
</script>

<style lang="scss">
	.wrap {
		width: 80vw;
		height: 90vh;
		margin-left: 10vw;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}

	.verification-button-text {
		font-weight: bold;
		border-radius: 10px;
		color: white;
		background-color: rgb(109, 95, 254);
		margin: 50rpx;
	}
</style>