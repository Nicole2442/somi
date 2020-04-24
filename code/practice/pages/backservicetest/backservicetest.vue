<template>
	<view>
		<button type="warn" @click="click">stop</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
			}
		},
		methods: {
			click(){
				uni.$emit('close','q')
			}
		},
		onLoad() {
		}
	}
</script>

<style>

</style>
