<template style="background-color: white;">
	<view class="logo-body">
		<view>
			<view style="height: 50rpx; width: 50rpx;margin-top: 50rpx;">
				<image src="../../static/yxg-logo.png" mode="aspectFit"
					style="border-radius: 50px;height: 100%;width: 100%;">
			</view>
			<view style="margin-top: 50rpx;">
				<u-text class="register-text" size="25" :bold="true" text="创建一个新的"></u-text>
			</view>
			<view style="margin-top: 50rpx;">
				<u-text class="register-text" size="25" :bold="true" text="YXG 账户"></u-text>
			</view>
			<u-line length="10%" color="rgb(255,126,118)" margin="10rpx 10rpx" :hairline="true"></u-line>
		</view>
		<view>
			<u-form :model="register" ref="ulogin">
				<u-text :color="textColor" text="姓名"></u-text>
				<u-form-item>
					<u-input v-model="register.name"></u-input>
				</u-form-item>
				<u-text :color="textColor" text="邮箱或手机"></u-text>
				<u-form-item>
					<u-input v-model="register.sign"></u-input>
				</u-form-item>
				<u-text :color="textColor" text="密码"></u-text>
				<u-form-item>
					<u-input type="password" :password-icon="true" v-model="register.passWord"></u-input>
				</u-form-item>
				<u-text :color="textColor" text="确认密码"></u-text>
				<u-form-item>
					<u-input type="password" :password-icon="true" v-model="register.checkPassWord"></u-input>
				</u-form-item>
				<u-form-item>
					<u-checkbox-group>
						<u-checkbox @change="checkAgreeOn" v-model="register.agreeOn" key="agreeOn" label="同意YXG客户端"
							:label-color="textColor" name="1"></u-checkbox>
						<u-text text="用户协议与隐私政策" color="rgb(74,70,224)" :bold="true" @click="showMessage"></u-text>
					</u-checkbox-group>
				</u-form-item>
				<u-form-item>
					<u-button class="logo-button-text" text="创建账户" @click="registerFunction"></u-button>
				</u-form-item>
			</u-form>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				textColor: "rgb(143,146,161)",
				register: {
					name: '',
					sign: '',
					passWord: '',
					agreeOn: false
				}
			};
		},
		methods: {
			checkAgreeOn(e) {
				console.log(e)
				this.register.agreeOn = e;
			},
			registerFunction() {
				console.log("注册");
				uni.navigateTo({
					url: "/pages/index/verification?name=" +
						this.register.name + "&" +
						"passWord=" + this.register.passWord + "&" +
						"sign=" + this.register.sign + "&" +
						"agreeOn=" + this.register.agreeOn
				})
			},
			showMessage() {
				console.log("协议");
			}
		}
	}
</script>

<style>
	.input-line {
		display: flex;
		flex-direction: column;
		align-items: stretch;
	}

	.logo-body {
		width: 80vw;
		height: 90vh;
		margin-left: 10vw;
		display: flex;
		flex-direction: column;
		justify-content: space-between;
	}

	.register-text {
		margin-top: 50rpx;
		margin-bottom: 50rpx;
	}

	.logo-button-text {
		font-weight: bold;
		border-radius: 10px;
		color: white;
		background-color: rgb(109, 95, 254)
	}
</style>