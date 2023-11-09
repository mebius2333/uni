<template>
	<view class="course_nav_con">
		<view class="course_nav_info" v-for="(item,index) in list" :key="index" @click="courseItemHandle(item.id,item.course)">
			<text class="course_nav_icon icon iconfont" :class="item.icon"></text>
			<view class="course_info_text">{{ item.text }}</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list: []
			}
		},
		mounted() {
			uni.request({
				url: "http://html5.bjsxt.cn/api/index/nav",
				success: (res) => {
					this.list = res.data.data
				}
			})
		},
		methods:{
			courseItemHandle(id,course){
				uni.navigateTo({
					url:"/pages/couser/courseIntroduce/courseIntroduce?id=" + id +"&course="+course
				})
			}
		}
	}
</script>

<style lang="scss">
	@import "@/common/font/iconfont.css";

	.course_nav_con {
		display: flex;
		// 盒子模型不撑开容器本身大小
		box-sizing: border-box;
		flex-direction: row;
		flex-wrap: wrap;
		padding: 15px 10px;

		.course_nav_info {
			width: 20%;
			flex-direction: row;
			flex-wrap: wrap;
			text-align: center;
			margin-bottom: 15px;

			.course_nav_icon {
				font-size: 30px;
			}

			.icon-java {
				color: #2a83fe;
			}

			.icon-weifuwu {
				color: #fd3761;
			}

			.icon-zuzhijiagou {
				color: #2b91e2;
			}

			.icon-dashuju {
				color: #2a83fe;
			}

			.icon-h {
				color: #00b478;
			}

			.icon-icon-- {
				color: #fd6012;
			}

			.icon-rengongzhineng {
				color: #fe391f;
			}

			.icon-ruanjianceshi {
				color: #00b478;
			}

			.icon-huatong {
				color: #fea917;
			}

			.icon-bianchengshibaobiao_icon {
				color: #2a83fe;
			}

			.icon-jianmo {
				color: #00b478;
			}

			.icon-chuangye {
				color: #fe391f;
			}

			.course_info_text {
				width: 100%;
				font-size: 13px;
				margin-top: 10px;
				white-space: nowrap;
				text-overflow: ellipsis;
				overflow: hidden;
			}
		}
	}
</style>
