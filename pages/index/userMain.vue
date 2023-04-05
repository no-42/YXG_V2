<template>
	<view>
		<view v-if="pageValue == 0">
			<view style="height: 50rpx; width: 50rpx;margin: 50rpx;">
				<image src="../../static/yxg-logo.png" mode="aspectFit"
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
				<u-text class="logo-text" size="25" :bold="true" text="个人中心"></u-text>
			</view>
			<u-line length="10%" color="rgb(255,126,118)" margin="30rpx" :hairline="true"></u-line>
			
			<u-avatar text="无头像"></u-avatar>
		</view>
		
		<u-tabbar :value="pageValue" @change="pageChange" :fixed="true" :placeholder="true" :safeAreaInsetBottom="true">
			<u-tabbar-item icon="home">
<!-- 				<image class="tabbar-item-img" slot="active-icon" src="../../static/homeActive.png"></image>
				<image class="tabbar-item-img" slot="inactive-icon" src="../../static/homeInactive.png"></image> -->
			</u-tabbar-item>
			<u-tabbar-item icon="bell">
				<!-- <image class="tabbar-item-img" slot="active-icon" src="../../static/messageActive.png"></image>
				<image class="tabbar-item-img" slot="inactive-icon" src="../../static/messageInactive.png"></image> -->
			</u-tabbar-item>
			<u-tabbar-item icon="account">
				<!-- <image class="tabbar-item-img" slot="active-icon" src="../../static/userrActive.png"></image>
				<image class="tabbar-item-img" slot="inactive-icon" src="../../static/userInactive.png"></image> -->
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
</style>