<template>
	<view class="">
		<!-- <view class="title">
			{{name}}
		</view> -->
		<view class="list">
			<uni-list>
				<uni-list-item :title="(index+1)+' '+item.title" note="" v-for="(item,index) in list" 
				clickable
				@click="handleClick(item)"
				></uni-list-item>
			</uni-list>
		</view>
	</view>
	
</template>

<script>
	export default{
		data(){
			return {
				list:[]
			}
		},
		methods:{
			handleClick(item){
				let url=item.url||item.link
				uni.navigateTo({
					url:`../webViewPage/index?url=${url}`
				})
			},
			setName(res){
				this.name=res
			},
			setLastModified(res){
				this.lastModified=res
			},
			setList(res){
				this.list=res
			}
		},
		onLoad(option){
			var that=this
			uni.request({
				url:'https://v2.alapi.cn/api/tophub',
				method:"POST",
				header:{
					"Content-Type":"application/x-www-form-urlencoded",
				},
				data:{
					"id":option.id,
					"token":"pKVLc1czEvYrCAjL",
				},
				
				success(res){
					
					res=res.data
					res=res.data
					console.log(res)
					// that.name=res.name
					// that.lastModified=res.last_update
					that.list=res.list
				}
			})
		},
	}
</script>

<style>
</style>
