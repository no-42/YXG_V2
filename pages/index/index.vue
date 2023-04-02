<template>
	<view style="width: '100vw', height: '100vh'">
		<image src="../../static/login.jpg" class="img" mode="center">
		</image>
		<view class="text-and-button">
			<view style="margin-bottom: 50rpx;">
				<h2 style="color: white;margin-bottom: 100rpx;">欢迎</h2>
				<u-text color="white" text="欢迎使用YXG客户端"></u-text>
				<u-text color="white" text="YXG 欢迎您"></u-text>
			</view>
			<view class="show-button">
				<u-button text="登录"
					style="margin-bottom: 20rpx;color:rgba(117,99,238);font-weight: bold;border-radius: 10px;"
					@click="toLogo"></u-button>
				<u-button style="color: white;font-weight: bold;border-radius: 10px;background:rgba(0,0,0,0);"
					text="创建新用户" @click="toRegister"></u-button>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
			};
		},
		onLoad() {},
		methods: {
			toRegister() {
				console.log("注册");
				uni.navigateTo({
					url:"/pages/index/register"
				})
			},
			toLogo() {
				console.log("登录");
				uni.navigateTo({
					url: "/pages/index/logo"
				})
			}
		}
	};
</script>
<style>
	.img {
		width: 100%;
		height: 100%;
		position: absolute;
	}

	.text-and-button {
		position: absolute;
		left: 50%;
		transform: translateX(-50%);
		width: 80%;
		bottom: 200rpx;
	}
</style>