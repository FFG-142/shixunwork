<template>
	<div class="bl-container bl-df-jcenter con-img">
		<div class="bl-col-8 left">
			<div class="bl-df-start">
			<h3>当前位置--></h3>
			<h3><a href="http://localhost:9090/#/index" >首页</a></h3>
			<h3>-->留言</h3>
		    </div>
			</br>
			<h2>我要留言：</h2>
			<div msgborder class="say-box">
				<div msgborder style="display: none;">
					
					<strong msgborder>回复：</strong>
					<span msgborder></span>
					<span msgborder title="取消回复" class="exit-aite">x</span>
					
				</div>
				<textarea msgborder placeholder="这人很懒啥都没写=v="></textarea>
				<input msgboard type="button"  value="留言" class="btn-n "
				 :class="{'shade':istrue === true}"
				 						 @mouseenter="stop"
				 						   @mouseleave="go"/>
			</div>
			</br>
			<div msgboard class="leavemsg">
			<div style="text-align: center;">
				<h2>所有留言：</h2>
			</div>
			<ul msgboard>
				<li msgboard class="board-item"></li>
				<div msgboard class="msg-leaver"></div>
			</ul>
			<div msgboard class="board-content"></div>
			
			
			
			</div>
			
		</div>
		<div class="bl-col-4 right">
			
		</div>
	</div>
</template>

<script>
	export default {
		data(){
			return {
				istrue:false
			}
		},
			methods:{
				stop(){
						this.istrue=true
					},
				go(){
					this.istrue=false
				}
			}
		
	}
</script>

<style>
	.msg-leaver {
	    display: -webkit-box;
	    display: -ms-flexbox;
	    display: flex;
	    -webkit-box-align: center;
	    -ms-flex-align: center;
	    align-items: center;
	}
	.board-item {
	    font-family: FangSong;
	    -webkit-box-sizing: border-box;
	    box-sizing: border-box;
	    padding: 5px 10px;
	    width: 100%;
	}
	.leavemsg {
	    margin-top: 32px;
	}
	.btn-n{
		width: 100px;
		height: 34px;
		outline: none;
		border: 1px solid #08D;
		color: #fff;
		padding:0 32px;
		text-align: center;
		font-size: 14px;
		border-radius: 10px;
	    background-color: rgb(74, 138, 244);
		margin-top: 10px;
		margin-left: 545px;
		cursor: pointer;
	}
	.shade{
		background-color: rgb(0, 121, 215);
	}
	.bottom-col{
		
	}
	
	.exit-aite {
	    margin-left: 5px;
	    color: #5bc0de;
	    cursor: pointer;
	}
	.msgboard {
	    background: #faf7f7;
	    margin-top: 10px;
	    padding: 20px 10px;
	    border-radius: 5px;
	    font-size: 14px;
	    color: #404040;
		}
	.say-box{
		margin: 10px 10px 5px;
	}
	.say-box textarea {
	    font-family: STFangsong;
	    resize: none;
	    overflow-y: none;
	    outline: none;
	    font-size: 14px;
	    padding: 5px;
	    border: none;
	    border-radius: 6px;
	    -webkit-box-sizing: border-box;
	    box-sizing: border-box;
	    width: 100%;
	    height: 100px;
	    -webkit-box-shadow: 0 0 8px rgba(0,0,0,.4);
	    box-shadow: 0 0 8px rgba(0,0,0,.4);
	}

	a, a:link {
		font-weight:bold;
	    color:rbg(26, 160, 52);
	    text-decoration: none;
		
	}
	a:hover{
		color: #FFD700;
	}
</style>
