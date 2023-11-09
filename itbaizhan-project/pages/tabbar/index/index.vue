<template>
	<view class="home">
		<Navbar />
		<view class="index_banner_box">
			<swiper class="swiper" :indicator-dots="true" :autoplay="true" :interval="3000" :duration="500">
				<swiper-item v-for="(item,index) in topBanner" :key="index">
					<image class="banner" :src="item.img_url" mode=""></image>
				</swiper-item>
			</swiper>
		</view>
		<CourseNav />
		<view class="online_box">
			<image :src="index_banner.img_url" class="online_img"></image>
		</view>
		<view class="free_box">
			<view class="free_T_box public_tow_box">
				<view class="public_T">
					限时免费
				</view>
			</view>
			<FreeCard />
		</view>
		<view class="public_title">
			<view class="public_class_t">零基础就业班</view>
			<JobScroll />
		</view>
		<view class="recommend_box">
			<view class="recommed_T_box public_tow_box">
				<view class="public_T">推荐课程</view>
			</view>
			<CourseCard />
		</view>
		<view class="daotu_box">
			<view class="daotu_T">驱动教学-贯穿教｜学｜练｜测｜评</view>
			<image :src="fontBanner.img_url" mode=""></image>
		</view>
	</view>
</template>

<script>
	import Navbar from "../../../components/navbar/navbar.vue"
	import CourseNav from "../../../components/coursenav/coursenav.vue"
	import FreeCard from "../../../components/free-card/free-card.vue"
	import JobScroll from "../../../components/jobscroll/jobscroll.vue"
	import CourseCard from "../../../components/course_card/course_card.vue"
	export default {
		data() {
			return {
				topBanner: [],
				index_banner:{},
				fontBanner:{}
			}
		},
		methods: {

		},
		mounted() {
			uni.request({
				url: "http://html5.bjsxt.cn/api/index/banner",
				// 注意
				success: (res) => {
					this.topBanner = res.data.top_banner
					this.index_banner = res.data.index_banner
					this.fontBanner = res.data.foot_banner
				}
			})
		},
		components: {
			Navbar,
			CourseNav,
			FreeCard,
			JobScroll,
			CourseCard
		}
	}
</script>

<style lang="scss">
	.home {
		display: flex;
		flex-direction: column;
		flex: 1;
		overflow: hidden;
		.index_banner_box {
			display: flex;
			width: 100%;
			padding: 10px;
			justify-content: center;
			align-items: center;
			border-radius: 5px;
			overflow: hidden;
			.swiper{
				width: 100%;
				height: 260rpx;
				.banner{
					width: 700rpx;
					height: 260rpx;
				}
			}
		}
		.online_box{
			display: flex;
			width: 724rpx;
			justify-content: center;
			align-items: center;
			box-sizing: border-box;
			overflow: hidden;
			margin-bottom: 15px;
			
			.online_img{
				width: 724rpx;
				height: 132rpx;
			}
			
		}
		.public_tow_box{
			display: flex;
			width: 100%;
			justify-content: center;
			align-items: center;
			box-sizing: border-box;
			overflow: hidden;
			padding: 0 15px;
			justify-content: space-between;
			align-content: space-between;
			flex-wrap: wrap;
			.public_T{
				font-size: 20px;
				font-weight: 700;
			}
		}
		.public_title{
			width: 100%;
			display: flex;
			padding: 0 15px;
			flex-direction: column;
			.public_class_t{
				font-size: 22px;
				font-weight: 700;
				margin-bottom: 15px;
			}
		}
		.recommed_T_box{
			margin-bottom: 25px;
		}
		
		.daotu_box{
			display: flex;
			box-sizing: border-box;
			flex-direction: column;
			justify-content: center;
			align-items: center;
			
			.daotu_T{
				font-size: 18px;
				font-weight: 700;
				margin: 15px ;
			}
			image{
				width: 699rpx;
				height: 634rpx;
				margin: 0 0 15px 0;
			}
		}
	}
</style>
