<template>
	<uni-collapse accordion>
		<uni-collapse-item v-for="(items,index) in arr" :title="items.name"showAnimation>
			<uni-list>
				<uni-list-item v-for="(item,index) in items.data" :title="item.name" 
					clickable
					@click="handleClick(item)"
				></uni-list-item>
			</uni-list>
		</uni-collapse-item>
	</uni-collapse>
</template>

<script>
	const res=[
			{	name:"综合榜单",
				data:[
					{
						name:"知乎热榜",
						id:"mproPpoq6O"
					},{
						name:"微博热榜",
						id:"KqndgxeLl9"
					},
					{
						name:"澎湃热榜",
						id:"wWmoO5Rd4E"
					},
					{
						name:"百度实时热榜",
						id:"Jb0vmloB1G"
					},
					{
						name:"知乎日报",
						id:"KMZd7VOvrO"
					},
					{
						name:"豆瓣话题广场",
						id:"LwkvlBqez1"
					},{
						name:"ZAKER 热榜",
						id:"5VaobJgoAj"
					},{
						name:"中国国家地理网 热榜",
						id:"6ARe1n6o7n"
					},{
						name:"新京报 热榜",
						id:"6ARe1n6o7n"
					},{
						name:"中国国家地理网 热榜",
						id:"YqoXQ8XvOD"
					},
					]
			},
			{	name:"科技榜单",
				data:[
					{
						name:"36氪 热榜",
						id:"Q1Vd5Ko85R"
					},{
						name:"少数派 热榜",
						id:"Y2KeDGQdNP"
					},
					{
						name:"果壳 热榜",
						id:"20MdK2vw1q"
					},
					{
						name:"虎嗅网 热榜",
						id:"5VaobgvAj1"
					},
					{
						name:"IT之家 热榜",
						id:"74Kvx59dkx"
					},
					{
						name:"爱范儿 热榜",
						id:"74KvxK7okx"
					},{
						name:"科普中国网 热榜",
						id:"DgeyxkwdZq"
					},{
						name:"中国国家地理网 热榜",
						id:"6ARe1n6o7n"
					},{
						name:"威锋网 热榜",
						id:"n4qv90roaK"
					},{
						name:"少数派 热榜",
						id:"NaEdZZXdrO"
					},
				]
			},
			{	name:"娱乐榜单",
				data:[
					{
						name:"哔哩哔哩 热榜",
						id:"74KvxwokxM"
					},{
						name:"抖音 热榜",
						id:"DpQvNABoNE"
					},
					{
						name:"豆瓣电影 热榜",
						id:"nBe0JLBv37"
					},
					{
						name:"开眼视频 热榜",
						id:"KqndgDmeLl"
					},
					{
						name:"煎蛋 热榜",
						id:"NRrvWq3e5z"
					},
					{
						name:"豆瓣小组 热榜",
						id:"WYKd6jdaPj"
					},{
						name:"微信读书 热榜",
						id:"anoppbRolZ"
					},{
						name:"AcFun 热榜",
						id:"qENeYpdY49"
					},{
						name:"书伴 热榜",
						id:"0MdKab8ow1"
					},{
						name:"TapTap 热榜",
						id:"6ARe1k2v7n"
					},
				]
			},
			{	name:"社区榜单",
				data:[
					{
						name:"吾爱破解 热榜",
						id:"NKGoRAzel6"
					},{
						name:"百度贴吧 热榜",
						id:"Om4ejxvxEN"
					},
					{
						name:"天涯 热榜",
						id:"Jb0vmmlvB1"
					},
					{
						name:"V2EX 热榜",
						id:"wWmoORe4EO"
					},
					{
						name:"虎扑社区 热榜",
						id:"G47o8weMmN"
					},
					{
						name:"水木社区 热榜",
						id:"rDgeyqeZqJ"
					},{
						name:"汽车之家 热榜",
						id:"YqoXQGXvOD"
					},{
						name:"CSDN论坛 热榜",
						id:"6ARe1n6o7n"
					},{
						name:"威锋网 热榜",
						id:"K7GdajgeQy"
					},{
						name:"携程攻略 热榜",
						id:"1VdJPYnoLQ"
					},
				]
			},
			{	name:"购物榜单",
				data:[
					{
						name:"淘宝 ‧ 天猫 ‧ 热销总榜",
						id:"yjvQDpjobg"
					},{
						name:"淘宝 ‧ 天猫 ‧ 每日爆款清单",
						id:"7Gdab3peQy"
					},
					{
						name:"什么值得买 ‧ 京东好价榜",
						id:"Y2KeDmQoNP"
					},
					{
						name:"什么值得买 ‧ 天猫好价榜",
						id:"NaEdZLXorO"
					},
					{
						name:"什么值得买 ‧ 好文原创榜",
						id:"K7GdagpoQy"
					},
					{
						name:"什么值得买 ‧ 白菜好价榜",
						id:"G2me3Rxdwj"
					},
					{
						name:"小红书 ‧ 社区精选",
						id:"L4MdA5ldxD"
					},
					{
						name:"拼多多 ‧ 今日爆单榜",
						id:"8Rv2k9ndLw"
					},
					{
						name:"拼多多 ‧ 实时热销榜",
						id:"ARe1QZ2e7n"
					},
					{
						name:"当当 ‧ 畅销图书榜",
						id:"QaqeEage9R"
					},
				]
			},
			{	name:"财经榜单",
				data:[
					{
						name:"第一财经 ‧ 新闻排行周榜",
						id:"0MdKam4ow1"
					},{
						name:"雪球 ‧ 今日话题",
						id:"X12owXzvNV"
					},
					{
						name:"财新网 ‧ 评论排行榜",
						id:"3QeLGVPd7k"
					},
					{
						name:"财新网 ‧ 点击排行榜",
						id:"x9ozBY7oXb"
					},
					{
						name:"华尔街见闻 ‧ 日排行",
						id:"G2me3ndwjq"
					},
					{
						name:"新浪财经新闻 ‧ 点击量排行",
						id:"rx9ozj7oXb"
					},{
						name:"星球日报 ‧ 日榜",
						id:"WYKd6EwvaP"
					},{
						name:"21财经 ‧ 热门",
						id:"4Kvx5R0dkx"
					},{
						name:"第一财经商业数据中心 ‧ CBNData资讯",
						id:"2KeDwZQdNP"
					},{
						name:"华尔街见闻 ‧ 最新资讯",
						id:"wWmoO8kv4E"
					},
				]
			},
			{	name:"开发榜单",
				data:[
					{
						name:"GitHub ‧ Trending Weekly",
						id:"Q1Vd5xKv85"
					},{
						name:"Github ‧ Trending JavaScript Today",
						id:"3moBYq9eN5"
					},
					{
						name:"CSDN ‧ 今日推荐",
						id:"n3moBVoN5O"
					},
					{
						name:"掘金 ‧ 全站本周最热",
						id:"QaqeEaVe9R"
					},
					{
						name:"掘金 ‧ 前端本周最热",
						id:"zQ0orpOd8B"
					},
					{
						name:"开源中国 ‧ 热门资讯",
						id:"rYqoXZzdOD"
					},{
						name:"开发者头条 ‧ 7天热门",
						id:"9JndkELo3V"
					},{
						name:"SegmentFault ‧ 每周精选",
						id:"BwdG0mMePx"
					},{
						name:"InfoQ中国 ‧ 7天热点",
						id:"K7GdabpeQy"
					},{
						name:"JavaScript Weekly ‧ 最新期刊",
						id:"Q1Vd5G8o85"
					},
				]
			},
		]
	export default {
		data() {
			return {
				arr:res,
				title: 'Hello',
				Img:'/static/logo.png',
				target:true,
				UrlSrc:'www.google.com',
			}
		},
		onLoad() {
			
		},
		methods: {
			handleClick(item){
				uni.navigateTo({
					url:`../hotList/hotList?id=${item.id}`
				})
			},
			clickOne(){
				uni.request({
					url:"https://v2.alapi.cn/api/new/wbtop",
					header:{
						"token":"pKVLc1czEvYrCAjL",
						"Content-Type":"application/x-www-form-urlencoded"
					},
					success(res){
						console.log(res)
					}
				})
			},
			clickTwo(){
				uni.request({
					url:"https://v2.alapi.cn/api/acg",
					method:"POST",
					header:{
						"token":"pKVLc1czEvYrCAjL",
						"Content-Type":"application/x-www-form-urlencoded",
					},
					
					success(res){
						console.log(res)
					}
				})
			}
		}
	}
</script>

<style>
	/* .content {
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
	} */
</style>
