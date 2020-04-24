<template>
	<view>
		<button class="btn_request" @click="btn_get_click">{{btn_text}}</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				'btn_text':'get'
			}
		},
		methods: {
			btn_get_click(){
				uni.request({
					url: 'https://unidemo.dcloud.net.cn/api/news',
					method: 'GET',
					data: {},
					success: res => {
						console.log(res.data);
					},
					fail: () => {},
					complete: () => {}
				});
			}
		}
	}
</script>

<style>

</style>
