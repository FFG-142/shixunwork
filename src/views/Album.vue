<template>
	<div>
		<h3>相册记录生活页面</h3>
		<form action="/api/upload" method="post" enctype="multipart/form-data">
		    <input type="file" name="filename">
		    <input type="submit" value="上传">
		</form>
	</div>
</template>

<script>
	export default {
		data(){
			
			return {
				user:{},
				userArticle : []
			}
		},
		created: function() {
			/* 获取网页地址url */
		    var query = window.location.href;
	        /* 锁定到最后一个"="的位置 */
			var i = query.lastIndexOf("=");
			/* 取出"="之后的字符串 */
			var id = query.substring(i+1);
			/* 获取对应作者id的信息 */
			this.axios.get('http://localhost:8080/api/upload' + id).then(res =>{			
				this.user = res.data.data;
			
			})
			
		
			
		},
		methods:{
			
		}
	}
	
	
</script>

<style scoped>
	
</style>
