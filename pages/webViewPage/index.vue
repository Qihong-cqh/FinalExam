<template>
	<view class="content">
		<web-view :src="url"></web-view>
	</view>
</template>

<script>
	export default {
	    onLoad: function (option) { //option为object类型，会序列化上个页面传递的参数
	        console.log("this is web-view component "+option.url); //打印出上个页面传递的参数。
	        // console.log(option.name); //打印出上个页面传递的参数。
			this.url=option.url
	    },
		data(){
			return{
				url:''
			}
		}
	}
</script>

<style lang="scss">
	
</style>
