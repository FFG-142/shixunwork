<template>
	<div class="container">
		<div class="media-wraaper">
			<div class="media" v-for="(article, index) in articles" :key="index">
				<div class="media-left">
					<!-- <img :src="'https://images.weserv.nl/?url='+ article.avatar" class="avatar-lg link" /> -->
					<router-link :to="{ path: '/article/' + article.id }"><img :src="'https://images.weserv.nl/?url='+article.avatar" class="avatar-lg link" /></router-link>
					<!-- <img :src="'https://images.weserv.nl/?url='+ article.avatar" class="bl-avatar-normal" /> -->
					<!-- <img :src="'https://images.weserv.nl/?url='+ user.avatar" class="bl-avatar-normal" /> -->
					<!-- <p class="sub-title">{{ article.title }}</p> -->
				</div>
				<div class="media-middle">
					<h2>{{ article.title }}</h2>
					<p>{{ article.concent }}</p>
					<p>
						<span>转发量:{{article.forwardAccount}}</span>
						<span>评论人数:{{article.commentAccount}}</span>
						<span>关注量{{article.likeAccount}}</span>
						<div v-for="(art, index) in articleList" :key="index">
						<p>
							<i class="iconfont" 
							:class="{'thumb-up':art.isThumbUp === true}"
							 @click="changeThumbUps(art)">&#xe611;</i>
							 
							<span>{{art.thumbUpCount}}人喜欢</span>
						</p>
						</div>
					</p>
				</div>
				<div class="media-right"><img :src="'https://images.weserv.nl/?url='+ article.avatar" /></div>
			</div>
		</div>
	</div>
</template>
<script>
export default {
	data() {
		return {
			articleList: [
				{
					"thumbUpCount": 628
				}
				
				],
			isThumbUp: false,
			articles:[]
			
			
			
		};
	},
	created() {
		this.axios.get('http://localhost:8080/article').then(res => {
			console.log(res.data.data);
			this.articles = res.data.data;
		})
		
	},
	
	computed: {
		// 解决403图片缓存问题
		getImages(_url) {
			if (_url) {
				let _u = _url.substring(8);
				return 'https://images.weserv.nl/?url=' + _u;
			}
		}
	},
	methods: {
		go() {
			this.timer = setInterval(() => {
				this.autoPlay()
			}, 3000)
		},
		stop() {
			clearInterval(this.timer)
			this.timer = null
		},
		
		changeThumbUps(art) {
			if (art.isThumbUp == true) {
				art.isThumbUp = false
				art.thumbUpCount--
			} else {
				art.isThumbUp = true
				art.thumbUpCount++
			}
		},
	}
	
};
</script>

<style scoped>
	@font-face {
	  font-family: 'iconfont';  /* project id 1432516 */
	  src: url('//at.alicdn.com/t/font_1432516_nfop571g10j.eot');
	  src: url('//at.alicdn.com/t/font_1432516_nfop571g10j.eot?#iefix') format('embedded-opentype'),
	  url('//at.alicdn.com/t/font_1432516_nfop571g10j.woff2') format('woff2'),
	  url('//at.alicdn.com/t/font_1432516_nfop571g10j.woff') format('woff'),
	  url('//at.alicdn.com/t/font_1432516_nfop571g10j.ttf') format('truetype'),
	  url('//at.alicdn.com/t/font_1432516_nfop571g10j.svg#iconfont') format('svg');
	}
	.iconfont {
		font-family: "iconfont" !important;
		font-size: 16px;
		font-style: normal;
		color: #aaa;
		-webkit-font-smoothing: antialiased;
		-webkit-text-stroke-width: 0.2px;
		-moz-osx-font-smoothing: grayscale;
	}
	
	.iconfont:hover {
		cursor: pointer;
	}
	.thumb-up {
		color: #FF0000;
	}
	
	.avatar-lg {
		display: inline-block;
		width: 85px;
		height: 85px;
		border-radius: 50%;
	}

.media-wraaper {
	width: 100%;
	height: 180px;
	padding: 10px;
}
.media {
	display: flex;
	align-items: stretch;
	justify-content: flex-start;
	border-bottom: 1px solid #ddd;
	border-radius: 5px;
	background-color: #fff;
	margin-bottom: 5px;
	padding-top: 5px;
}
.media-left {
	flex: 0 0 15%;
	text-align: center;
	line-height: 50px;
	border-right: 1px solid #eee;
}
.media-middle {
	flex: 1 1 60%;
	padding-left: 10px;
	padding-right: 10px;
	line-height: 24px;
}
.media-middle h4 {
	font-weight: 600;
}
.media-middle p {
	font-size: 14px;
	color: #aaa;
}
.media-right {
	flex: 0 0 20%;
	text-align: center;
	margin-right: 10px;
}
.media-right img {
	width: 120px;
	height: 100px;
	border-radius: 10px;
}
</style>