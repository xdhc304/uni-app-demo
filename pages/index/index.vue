<template>
	<view class="content">
		<view class="header">
			<image class="logo" src="/static/logo.png"></image>
		</view>
		<view>
			<swiper class="swiper" indicator-dots="true" autoplay="true" interval="3000" duration="500">
					<swiper-item :key="index" v-for="(item, index) in bannerList">
							<image class="banner" :src="item.cycleUrl"></image>
					</swiper-item>
			</swiper>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				bannerList: []
			}
		},
		onLoad() {
			this.getData();
		},
		methods: {
			getData() {
				uni.request({
				    url: 'http://47.99.222.45:8089/api/cycle_url_list', //仅为示例，并非真实接口地址。
				    data: {
				        // text: 'uni.request'
				    },
				    header: {
				        // 'custom-header': 'hello' //自定义请求头信息
				    },
				    success: (res) => {
				        console.log(res.data);
								this.bannerList = res.data.data;
				    }
				});
			}
		}
	}
</script>

<style>
	.content {
	}
	
	.header {
		height: 60px;
		background: #383D41;
	}
	
	.logo {
		width: 150px;
		height: 100%;
		padding-left: 5px;
	}

	.banner {
		width: 100%;
		height: 150px;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
</style>
