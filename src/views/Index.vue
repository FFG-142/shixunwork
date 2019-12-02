<template>
	<div class="bl-container bl-df-jcenter backg">
		<div class="bl-col-8 left">
			<!-- 主页轮播 -->
			<div class="head">
				<div class="carousel-wrap">
					<transition-group tag="ul" class="slide-ul" name="slide">
						<li v-for="(art,index) in avatars" :key="index" v-show="index===currentIndex" @mouseenter="stop" @mouseleave="go">
							
								<img :src="art">
<!-- 								<div class="welldown">
									<div class="a-color">
										我所学到的所有有价值的知识都是由自学中得来的
									</div>
									</br>
									<div class="a-color name-pos">---达尔文</div>
									
								</div> -->
						</li>
					</transition-group>
					<div class="carousel-items">
						<span v-for="(art,index) in avatars" :class="{active:index===currentIndex}" @mouseover="change(index)"></span>
					</div>
					
				</div>
				
			</div>
			<p class="bl-title">文章推荐</p>
			<hr>
					<div v-for="(item, index) in articles" :key="index" class="col-12">
								<div class="bl-article-recommendation bl-df-center ">
										<router-link :to="{ path: '/article/' + item.article.id }" class="subtitle">
											 {{ item.article.title }} 
										</router-link>
										<p class="sub-title link">{{ item.article.summary }}</p>
										<p>
											<span class="meta gutter">{{ item.article.comments }}评论</span>
											<span class="meta">{{ item.article.likes }}喜欢</span>
										</p>
									</div>
									<div class="media-right"><img :src="item.article.thumbnail" alt=""  class="ar-avatar"/></div>
								</div>
<!-- 			<div class="bl-card" v-for="(article, index) in articles.slice(0,4)" :key = "index">
				
				<div class="bl-article-recommendation bl-df-center ">
					<router-link :to="{ path: '/article/' + article.id }"><img :src="'https://images.weserv.nl/?url='+article.thumbnail" class="ar-avatar" /></router-link>
					<div class="ar-avatar" >
						<img :src = "'https://images.weserv.nl/?url='+article.thumbnail" >
					</div> -->
					<!-- 
					<div class="ar-right bl-df-c-center">
						
						<p class="bl-title">{{article.title}}</p>
						<p class="article-description">{{article.summary}}</p>
						<p class="ar-comment bl-df-between">
							<ul>
								<span>个人博客</span>
							    <span>
								     创建时间:{{article.createTime.date.year}}-{{article.createTime.date.month}}-{{article.createTime.date.day}}
								</span>
							</ul>
							<ul>
							     <span>转发量:{{article.forwardAccount}}</span>
							     <span>评论人数:{{article.commentAccount}}</span>
							     <span>关注量{{article.likeAccount}}</span>
								 
							</ul>
						</p>
					</div>
				</div>
			<hr class="split-line">
			</div> --> -->
		</div>
		<div class="bl-col-4 right">
			<!-- <div class="bl-df-c-center" v-for="(users, index) in users.slice(0,3)" :key = "index">
			<div class = "bl-right-sideCard bl-df-left">
				<div class="bl-content-avatar" @click="jump-personal">
					<img :src="'https://images.weserv.nl/?url='+ users.avatar" class="bl-btn-circle" alt="" @click="gotoPersonalDetail(users.id)">
				</div>
				<div class="bl-df-c-center">
					<p class="bl-md-font bl-bd-font">{{users.nickname}}</p>
					<p class="bl-msm-font user-descripiton">{{users.introduction.substring(0,30)+"..."}}</p>
					<p class="bottom bl-df-between">
						<span>文章数：13</span>
						<span>粉丝量:{{users.fans}}</span>
					</p>
				</div>
			</div>
			</div> -->
			<div class="board">
				<a href="/profile">
					<img src="//cdn2.jianshu.io/assets/web/banner-s-club-aa8bdf19f8cf729a759da42e4a96f366.png" class="board-img">
				</a>
				<a href="/profile">
					<img src="//cdn2.jianshu.io/assets/web/banner-s-7-1a0222c91694a1f38e610be4bf9669be.png" class="board-img">
				</a>
				<a href="/profile">
					<img src="//cdn2.jianshu.io/assets/web/banner-s-5-4ba25cf5041931a0ed2062828b4064cb.png" class="board-img">
				</a>
				<a href="/profile">
					<img src="//cdn2.jianshu.io/assets/web/banner-s-6-c4d6335bfd688f2ca1115b42b04c28a7.png" class="board-img">
				</a>
				
			</div>
			
			
			
			
			<div>
				<h2>最新热门</h2>
				
			</div>
			<div class="bl-df-c-center" v-for="(users, index) in users.slice(0,3)" :key = "index">
			<div class = "bl-right-sideCard bl-df-left">
				<div class="bl-content-avatar" @click="jump-personal">
					<img :src="'https://images.weserv.nl/?url='+ users.avatar" class="bl-btn-circle" alt="" @click="gotoPersonalDetail(users.id)">
				</div>
				<div class="bl-df-c-center">
					<p class="bl-md-font bl-bd-font">{{users.nickname}}</p>
					<p class="bl-msm-font user-descripiton">{{users.introduction.substring(0,30)+"..."}}</p>
					<p class="bottom bl-df-between">
						<span>文章数：{{users.articles}}</span>
						<span>粉丝量:{{users.fans}}</span>
						
					</p>
				</div>
			</div>
			</div>
			<div>
				<ul class="u-flex">
					<li class="bottom-size bottom-color avatar">
						<bottom>express</bottom>
					</li>
					<li class="bottom-size bottom-color1 avatar">
						<bottom>mongo</bottom>
					</li>
					<li class="bottom-size bottom-color avatar">
						<bottom>express</bottom>
					</li>
					<li class="bottom-size1 bottom-color1 avatar v-c">
						<bottom>vue</bottom>
					</li>
					<li class="bottom-size1 bottom-color avatar v-c">
						<bottom>css</bottom>
					</li>
					</ul>
			</div>
			
			
			</div>
		</div>
</template>

<script>
	export default {
		data() {
			return {
				articles : [],
				users : [],
				avatars : [
					"https://img.mukewang.com/5dceaccf0001f22c18720764.jpg",
				    "https://img.mukewang.com/5dd1fe8800013d1818720764.jpg",
					"https://img.mukewang.com/5dd4ad330001065518720764.jpg",
					"https://img.mukewang.com/5ddb345f00016ca218720764.jpg",
					"https://img.mukewang.com/5dce78c20001e39918720764.jpg",
				],
				
				currentIndex: 0,
				timer: null,
				
				user: JSON.parse(localStorage.getItem('user'))
			}
		},
		created : function() {
			
			/* 查询所有文章 */
			this.axios.get('http://localhost:8080/api/article').then(res=>{
			this.articles = res.data.data;
			}),
			
			/* 动画自动播放 */
			this.$nextTick(() => {
				this.timer = setInterval(() => {this.autoPlay()}, 3000)
			}),
			
			/* 查询所有用户 */
			this.axios.get('http://localhost:8080/api/user').then(res =>{
				this.users = res.data.data;
				console.log(res.data.data);
			})
		},
		
		methods:{
			change(index) {
				this.currentIndex = index
			},
			gotoPersonalDetail(id) {
				 this.$router.push('/persondeatil?id=' + id);
			},
			gotoArticleDetail(id) {
				 this.$router.push('/articledeatil?id=' + id);
			},
			go() {
				this.timer = setInterval(() => {
					this.autoPlay()
				}, 3000)
			},
			stop() {
				clearInterval(this.timer)
				this.timer = null
			},
			autoPlay() {
				this.currentIndex++
				if (this.currentIndex > 4) {
					this.currentIndex = 0
				}
			},
			
		}
	}
</script>

<style scoped>
	.v-c{
		text-align: center;
	}
	.u-flex{
		display: flex;
		margin-left: -30px;
	}
	.u-flex1{
		display: flex;
		margin-top: 10px;
	}
	.avatar{
		width: 100px;
		height: 100px;
		transition: all 1s;
		
		margin: 0 -20px;
		vertical-align: center;
	}
	.avatar:hover{
		transform: scale(1.1);
		opacity: 0.7;
		cursor: pointer;
	}
	.active {
		
		color: #00BBDD;
		font-weight: 600;
		/* border-bottom: 2px solid #00BBDD; */
	}
	.bottom-size{
		margin-left: 30px;
		height: 27px;
		width: 59px;
		border-radius: 5px;
	}
	.bottom-size1{
		margin-left: 30px;
		height: 27px;
		width: 45px;
		border-radius: 5px;
	}
	.bottom-color{
		background-color: #2196F3;
	}
	.bottom-color1{
		background-color:rgb(26, 160, 52);
	}
	.bottom-color2{
		background-color: rgb(220, 75, 62);
	}
	.con-img{
		background-color: ;
	}

	.board{
		border-radius:50% ;
	}
	.board-img{
		width: 340px;
		height: 60px;
		margin:0 auto;
	}
	.item-wrapper {
		display: flex;
		background-color: #fff;
		border: 1px solid #eee;
		border-radius: 5px;
		margin: 10px;
	}
	.left {
		padding: 20px 20px ;
		background: rgba(144,202,249,0.8);
		border:2px solid #42a5f5;
	}
	.right {
		margin: 0;
		height: 800px;
		background: rgba(144,202,249,0.8);
		border:2px solid #42a5f5;
	}
	
	.head {
		width: 100%;
		height: 260px;
		margin-bottom: 20px;
		
	}
	
	.head img {
		width: 100%;
		height: 100%;
	}
	
	hr {
		margin-top: 10px;
		margin-bottom: 10px;
		border: 2px solid #DDDDDD;
		width: 100%;
	}
	
	p {
		margin-top: 5px;
	}
	
	ul span {
		
		margin-left: 10px;
	}
	
	.ar-title {
		height: 30px;
		width: 100%;
	}
	.ar-avatar {
		width: 180px;
		height: 140px;
		border: 1px solid #009688;
	}
	
	.ar-avatar img {
		width: 100%;
		height: 100%;
	}
	
	.ar-right {
		height: 100%;
		width: 100%;
		padding: 10px 10px;
	}
	
	.article-description {
		width: 100%;
		margin-top: 10px;
		height: 120px;
		font-size: 12px;
		line-height: 20px;
		font-family: "雅黑";
	}
	
	.ar-comment {
		margin-top: 10px;
		width: 100%;
		font-size: 12px;
	}
	
	.split-line {
		margin-top: 30px;
		border: 0.5px solid;
	}
	
	.bottom {
		font-size: 12px;
		width: 200px;
	}
	
	.user-descripiton {
		height: 30px;
	}
	.welldown{
		z-index: 100;
		position: absolute;
		top: 60px;
		width: 80%;
	    left: 60px;
		
	}
	.a-color{
		color: #FFFFFF;
	}
	.name-pos{
		position: absolute;
		top: 100px;
		left: 200px;
	}
	.carousel-items1{
		z-index: 100;
		position: relative;
		top: 20px;
		text-align: center;
		font-size: 0;
	}
	.carousel-items {
		z-index: 100;
		position: relative;
		top: -20px;
		text-align: center;
		font-size: 0;
	}
	
	.carousel-items span {
		display: inline-block;
		width: 8px;
		height: 8px;
		margin: 0 5px;
		background-color: #eee;
		border-radius: 5px;
		cursor: pointer;
	}
	
	.carousel-items .active {
		width: 30px;
		background-color: #FFA500;
	}
	/* 动画 */
	.slide-enter-to {
		transition: all 1s ease;
		transform: translateX(0);
	}
	
	.slide-leave-active {
		transition: all 1s ease;
		transform: translateX(-100%)
	}
	
	.slide-enter {
		transform: translateX(100%)
	}
	
	.slide-leave {
		transform: translateX(0)
	}
	
</style>
