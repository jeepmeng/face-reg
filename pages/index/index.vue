<template>
	<view class="content">
		<image class="logo" src="/static/logo.png"></image>
		<view class="text-area">
			<text class="title">{{title}}</text>
		</view>
	</view>
</template>

<script>
	import * as faceapi from 'face-api.js';
	export default {
		data() {
			return {
				title: 'Hello'
			}
		},
	  async onLoad() {
		await this.loadModels();
	  },
	  methods: {
		async loadModels() {
		  // 引入 face-api.js 脚本
		  // const script = document.createElement('script');
		  // script.src = '/static/js/face-api.min.js';
		  // document.head.appendChild(script);

		  script.onload = async () => {
			// 加载模型
			await faceapi.nets.tinyFaceDetector.loadFromUri('/static/models');
			await faceapi.nets.faceLandmark68Net.loadFromUri('/static/models');
			await faceapi.nets.faceRecognitionNet.loadFromUri('/static/models');
			console.log('Models loaded');
		  };
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
