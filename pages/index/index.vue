<template>
	<view class="content">
		<!-- <image class="logo" src="/static/logo.png"></image>
		<view class="text-area">
			<text class="title">{{title}}</text>
		</view> -->
		
		<view class="search">
			<input value="test" maxlength="200" class="search_input" />
			<button class="search_button">搜索</button>
		</view>
		
		<view class="check_box_div">
			<checkbox-group >
				<label>
					<view class="uni-flex uni-row">
						<view class="content">
							<checkbox value="cb" checked="true" style="transform:scale(0.7)" />
						</view>
						<view class="content"><text class='check_box_p'>网站四</text></view>
						
					</view>
					<checkbox value="cb" checked="true" />网站1
					</label>
				<label>
					<checkbox value="cb" style="transform:scale(0.7)" /> 网站2
				</label>
				<label>
					<checkbox value="cb" style="transform:scale(0.7)" /> 网站3
				</label>
				
			</checkbox-group>
		</view>
		
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello'
			}
		},
		onLoad() {

		},
		methods: {

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
	
	.search {
		display: flex;
		flex-direction: row;
		margin-top: 100rpx;
	}
	
	.search_button {
		align-items: flex-start;

	}
	
	.search_input {
		outline-style: none ;
		border: 1px solid #ccc; 
		border-radius: 3px;
		padding: 8rpx;
		width: 320px;
		font-size: 24px;
	}
	
	.check_box_div {
		margin-top: 100rpx;
	}
	
	.check_box_p {
		font-size: 10rpx;
		align-items: flex-start;
	}
	
</style>
