<template>
	<view class="">
		
	
	<uni-collapse accordion>
		<uni-collapse-item :title="items.name" v-for="(items,index) in arr" showAnimation>
			<view class="collapse-content">
				<button 
				type="default" 
				v-for="(item,index) in items.data" 
				:key="index" 
				size="mini"
				@click="handleClick(item)" 
				class="content-button">
				{{item.name}}</button>
			</view>
		</uni-collapse-item>
	</uni-collapse>
	
	<uni-popup ref="popup" type="center">
		<view class="mypopup">
			{{content}}
		</view>
	</uni-popup>
	<uni-popup ref="popupImg" type="center">
		<view class="mypopupImg">
			<image :src="ImgSrc" mode="aspectFit"></image>
		</view>
	</uni-popup>
	</view>
</template>

<script>

const res=[
	{name:'文字工具',
	data:[
		{name:"动心一言",url:'https://v2.alapi.cn/api/hitokoto'},
		{name:"心灵毒鸡汤",url:'https://v2.alapi.cn/api/soul'},
		{name:"土味情话",url:'https://v2.alapi.cn/api/qinghua'},
		{name:"舔狗日记",url:'https://v2.alapi.cn/api/dog'},
		{name:"名人名言",url:'https://v2.alapi.cn/api/mingyan'},
		{name:"随机诗词",url:' https://v2.alapi.cn/api/shici'},
		],
	},
	{name:'图片工具',
	data:[
		{name:"每日一图",url:'https://v2.alapi.cn/api/bing'},
		{name:"ACG图片",url:' https://v2.alapi.cn/api/acg'},
	],
	// *** 生活工具
	// 垃圾分类查询
	// 天气预报 echarts
	// 中英翻译
	// 快递查询
	},
]

export default {
	data(){
		return{
			arr:res,
			content:'this is my content',
			author:'',
			title:"",
			from:'',
			ImgSrc:""
		}
	},
	methods:{
		handleClick(item){
			let that=this
			if(item.name==="每日一图"||item.name==="ACG图片"){
				uni.request({
					url:item.url,
					method:"POST",
					header:{
						"token":"pKVLc1czEvYrCAjL",
						"Content-Type":"application/x-www-form-urlencoded"
					},
					data:{
						"format":"json"
					},
					success(res){
						res=res.data
						res=res.data
						console.log(res)
						that.ImgSrc=res.url
						that.$refs.popupImg.open()
					}
				})
			}else{
				uni.request({
					url:item.url,
					method:"GET",
					header:{
						"token":"pKVLc1czEvYrCAjL",
						"Content-Type":"application/x-www-form-urlencoded"
					},
					success(res){
						res=res.data
						res=res.data
						console.log(res)
						that.content=res.hitokoto||res.title||res.content||""
						that.from=res.from||""
						that.author=res.creator||""||res.author
						that.title=res.origin||""
						that.$refs.popup.open()
					}
				})
			}
		}
	}
}
</script>

<style lang="scss">
	.collapse-content{
		margin:10rpx 16rpx;
		display: flex;
		flex-direction: row;
		flex-wrap: wrap;
		.content-button{
			margin:10rpx 8rpx;
			border-radius: 10rpx;
		}
	}
	.mypopup{
		height:50vh;
		width:70vw;
		background:#ffffcc;
		border-radius: 10rpx;
		overflow: auto;
	}
</style>
