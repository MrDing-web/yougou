<template>
	<view>
		<search />
		<swiper autoplay indicator-dots circular class="banner">
			<swiper-item v-for="item in bannerList" :key="item.goods_id">
				<navigator :url="item.navigator_url"><image :src="item.image_src" class="banner_img"></image></navigator>
			</swiper-item>
		</swiper>
		<view class="navMenu">
			<navigator class="navMenuItem" v-for="item2 in navList" :key="item2.name" url="pages/category/index"><image :src="item2.image_src" mode="widthFix"></image></navigator>
		</view>
		<view class="floor">
			<view class="floor_category" v-for="item in floorList" :key="item.floor_title.name">
				<image class="floor_category_item_title" :src="item.floor_title.image_src" mode="widthFix"></image>
				<view class="floor_content">
					<navigator class="floorNav" url="" v-for="item2 in item.product_list" :key="item2.name" >
						<image :src="item2.image_src" class="floor_img"></image>
					</navigator>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
import search from '@/components/search.vue';

export default {
	components: {
		search
	},
	data() {
		return {
			title: 'Hello',
			bannerList: [],
			navList: [],
			floorList: []
		};
	},
	onLoad() {
		uni.request({
			url: 'https://api-hmugo-web.itheima.net/api/public/v1/home/swiperdata'
		}).then(res => {
			this.bannerList = res[1].data.message;
		});
		uni.request({
			url: 'https://api-hmugo-web.itheima.net/api/public/v1/home/catitems'
		}).then(res => {
			this.navList = res[1].data.message;
		});
		uni.request({
			url: 'https://api-hmugo-web.itheima.net/api/public/v1/home/floordata'
		}).then(res => {
			this.floorList = res[1].data.message;
		});
	},
	methods: {}
};
</script>

<style lang="scss">
.banner {
	height: 340rpx;
	.banner_img {
		height: 340rpx;
	}
}

.navMenu {
	display: flex;

	.navMenuItem {
		flex: 1;
		display: flex;
		justify-content: center;
		align-items: center;
		margin: 20rpx 0;

		image {
			width: 70%;
		}
	}
}

.floor {
	width: 750rpx;
	.floor_category {
		width: 100%;
		.floor_category_item_title {
			width: 100%;
			padding: 24rpx 0;
		}
		.floor_content {
			width: 750rpx;
			overflow: hidden;
			.floorNav {
				display: block; 
				float: left;
				width: 32.62%;
			}
			.floorNav:nth-child(1){
				height: 386rpx;
			}
			.floorNav:nth-child(2){
				height: 189rpx;
				border-left:8rpx solid #fff;
				border-bottom:8rpx solid #fff;
				
			}
			.floorNav:nth-child(3){
				height: 189rpx;
				border-left:8rpx solid #fff;
				border-bottom:8rpx solid #fff ;
				
			}
			.floorNav:nth-child(4){
				height: 189rpx;
				border-left:8rpx solid #fff;
				
			}
			.floorNav:nth-child(5){
				height: 189rpx;
				border-left:8rpx solid #fff;
			}
			.floor_img{
				width: 100%;
				height: 100%;
			}
		}
	}
}
</style>
