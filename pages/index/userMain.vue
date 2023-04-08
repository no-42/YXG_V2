<template>
	<view>
		<view v-if="pageValue == 0">
			<view style="height: 50rpx; width: 50rpx;margin: 50rpx;">
				<image src="../../static/yxg-logo-2.png" mode="aspectFit"
					style="border-radius: 50px;height: 100%;width: 100%;">

			</view>
			<view style="margin: 50rpx;">
				<u-text class="logo-text" size="25" :bold="true" text="上午好,领航员"></u-text>
			</view>
			<u-line length="10%" color="rgb(255,126,118)" margin="50rpx" :hairline="true"></u-line>
		</view>


		<view v-if="pageValue == 1">
			<view style="margin: 50rpx;">
				<u-text class="logo-text" size="25" :bold="true" text="消息通知"></u-text>
			</view>
			<u-line length="10%" color="rgb(255,126,118)" margin="30rpx" :hairline="true"></u-line>
		</view>

		<view v-if="pageValue == 2">

			<view style="margin: 50rpx;">
				<u-row>
					<u-col span="10">
						<u-text class="logo-text" size="25" :bold="true" text="个人中心"></u-text>
					</u-col>
					<u-col span="2" style="height: 50rpx; width: 50rpx;">
						<u-icon name="scan" size="30"></u-icon>
					</u-col>
				</u-row>
			</view>
			<u-line length="10%" color="rgb(255,126,118)" margin="30rpx" :hairline="true"></u-line>
			<view style="margin: 50rpx;">
				<view style="margin-top: 20rpx;margin-bottom: 20rpx;height: 300rpx;">
					<u-row style="background-image: url('../../static/login.jpg');height: 100%;border-radius: 20px;">
						<u-col span="6">
							<u-avatar text="无头像" size="80" mode="aspectFit" style="margin-left: 20rpx;"></u-avatar>
						</u-col>
						<u-col span="6">
							<u-text size="25" :bold="true" color="white" text="用户名"></u-text>
						</u-col>
					</u-row>
				</view>
				<u-cell-group>
					<u-cell title="服务" :isLink="true">
						<u-icon slot="icon" size="32" name="../../static/yxg-logo-2.png"
							style="border-radius: 50px;height: 100%;width: 100%;"></u-icon>

					</u-cell>
					<u-cell title="卡包" :isLink="true">
						<u-icon slot="icon" size="32" name="../../static/pack.png"></u-icon>

					</u-cell>
					<u-cell title="设置" :isLink="true">
						<u-icon slot="icon" size="32" name="../../static/setting.png"></u-icon>

					</u-cell>

				</u-cell-group>
			</view>

		</view>

		<u-tabbar :value="pageValue" @change="pageChange" :fixed="true" :placeholder="true" :safeAreaInsetBottom="true">
			<u-tabbar-item icon="home">
			</u-tabbar-item>
			<u-tabbar-item icon="bell">
			</u-tabbar-item>
			<u-tabbar-item icon="account">
			</u-tabbar-item>
		</u-tabbar>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				pageValue: 0
			}
		},
		methods: {
			pageChange(e) {
				this.pageValue = e;
				console.log(e);
			}
		}
	}
</script>

<style>
	.tabbar-item-img {
		width: 40rpx;
		height: 40rpx;
	}

	.img {
		width: 100%;
		height: 100%;
		position: absolute;
	}
</style>