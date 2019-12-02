<template>
	<div class="backg1">
	<div class="bl-df-center">
		 
		<div class="login-box bl-shadow ">
			<div class="header bl-df-c-jcenter">
				
				
				<div>账号:<input type="text" placeholder="请输入手机号" class="bl-input-box" v-model="userDto.mobile"></div>
				<div>密码:<input type="password" placeholder="请输入密码" class="bl-input-box" v-model="userDto.password"></div>
				<div>验证码:<input type="text" v-model="userDto.code" placeholder="请输入验证码" class="bl-input-box"></div>
<!-- 				<img class="code-size" @click.prevent="refresh" ref="codeImg" /> -->
							 <!-- <div class="code-size">
							 <img src="http://localhost:8080/api/code" />
				             </div>  	
				            </div> -->

			</div>
			<div class="body bl-df-center place">
				<button class="bl-btn bl-btn-round bl-btn-default bl-btn-nomar bl-shadow" @click="signIn(userDto)">登录</button>
				<button class="bl-btn bl-btn-round bl-btn-warning bl-btn-nomar bl-shadow" @click="register()">注册</button>
			</div>
		</div>
	</div>
	</div>
</template>

<script>
	
	export default {
	  data() {
		 
		  
	    return {
	      userDto: {
	        mobile: '',
	        password: '',
		    code:''
	      }
	    };
	  },
	  created() {
	  		this.axios.get(this.GLOBAL.baseUrl + '/api/code', { responseType: 'blob' }).then(res => {
	  			// console.log(res);
	  			var img = this.$refs.codeImg;
	  			let url = window.URL.createObjectURL(res.data);
	  			img.src = url;
	  			console.log(res.headers);
	  			//取得后台通过响应头返回的sessionId的值
	  			this.token = res.headers['access-token'];
	  			console.log(this.token);
	  		});
	  	},
	  methods: {
	    signIn(userDto) {
	      this.axios.post('http://localhost:8080/sign-in', JSON.stringify(this.userDto)).then(response => {
	        alert(response.data.msg);
	        if (response.data.msg === '登录成功') {
	          //将后台的用户信息存入本地存储
	          localStorage.user = JSON.stringify(response.data.data);
			  //路由跳转
	          this.$router.push('/personal/basic');
	        }
	      });
	    },
		register(){
			this.$router.push('/personal/basic');
		},
		refresh() {
					this.axios.get(this.GLOBAL.baseUrl + '/api/code', { responseType: 'blob' }).then(res => {
						console.log(res);
						var img = this.$refs.codeImg;
						let url = window.URL.createObjectURL(res.data);
						img.src = url;
					});
					}
	  },
	  
	};
</script>


<style scoped>
	.backg1{
		background-color: rgba(226,219,190,0.8);
	}
	.code-size{
		width: 100px;
		height: 60px;
	}
	.pic-img{
		width: 150px;
		height: 40px;
	}
     .login-box {
		 margin-top: 200px;
            width: 400px;
            height: 400px;
            padding: 10px 5px 5px 10px;
            background-color: rgba(144,202,249,0.9);
            border: 1px solid #ddd;
            border-radius: 20px;
            box-shadow: 2px 5px 10px #aaa;
            text-align: center;
        }

	
	.header {
		margin-top: 30px;
		height:200px ;
		width: 400px;
	}
	.place{
		position: absolute;
		top: 520px;
		left: 810px;
	}
</style>
