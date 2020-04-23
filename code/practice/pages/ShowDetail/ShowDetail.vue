<template>
	<view>
		<text>{{text}}</text>
	</view>
</template>

<script>
	import airport from'../../common/airport.js'
	export default {
		data() {
			return {
				text: airport.list[1].data[1]
			}
		},
		onLoad() {
			
		},
		methods: {
		}
	}
</script>

<style>

</style>
