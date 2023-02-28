<template>
	<view class="content">
		<view v-for="(res,key) in imgArr" :key="key">
			<image class="logo" :src="res.url"></image>
		</view>
		<view class="text-area">
			<button type="default" @click="goPreview(imgArr,key)">点击生成分享图</button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				imgArr: [{
						"url": 'https://gitee.com/jiao_qianjin/zhishiku/raw/master/img/20200722164518.png'
					},
					{
						"url": 'https://gitee.com/jiao_qianjin/zhishiku/raw/master/img/20200722164518.png'
					},
					{
						"url": 'https://gitee.com/jiao_qianjin/zhishiku/raw/master/img/20200722164518.png'
					}
				]
			}
		},
		onLoad() {

		},
		methods: {
			goPreview(imgArr, val) {
				const urls = imgArr;
				const current = val;
				console.log(urls,current)
				uni.previewImage({
					current,
					urls,
					longPressActions: {
						itemList: ['发送给朋友', '保存图片', '收藏'],
						success: function(data) {
							console.log('选中了第' + (data.tapIndex + 1) + '个按钮,第' + (data.index + 1) +
								'张图片');
						},
						fail: function(err) {
							console.log(err.errMsg);
						}
					}
				})
			}
		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
</style>
