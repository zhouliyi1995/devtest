<template>
  <div class="container" style="background-color:#f9f9f9" id="idx">
    <div class="navwrap">
      <div class="nav" @click='scrollToBottom'>
        <div class="logowrap">
          <img src="../assets/images/logo.png">
        </div>
        <div class="navhide" @click="navshow"></div>
        <div class="navph" :class="{'active':collapse}">
        	<div class="tabs">
          <el-menu :default-active='activeIndex' router class="el-menu-demo" mode="horizontal"  active-text-color='#409eff'>
          <el-menu-item :index="item.path" v-for='item in menus'><span>{{item.name}}</span></el-menu-item>
          </el-menu>
        </div>
        <div class="buttons">
          <el-button type="primary" @click='login'>登录</el-button>
          <el-button plain  @click.native.prevent="handleRegister">注册</el-button>
        </div>
        </div>

      </div>
    </div>
    <router-view/>
  </div>
</template>

<script>
import '@/utils/jquery'
export default {
  name: 'index',
  data () {
    return {
      activeIndex: '/index/product',
      menus: [
        {
          name: '首页',
          path: '/index/product'
        }, {
          name: '对接资源',
          path: '/index/resource'
        },
        {
          name: '联系我们',
          path: '/index/contact'
        }
      ],
      collapse:true
    }

  },
  methods: {
    scrollToBottom(){
        var container=$(".container").scrollTop()
        // var container=document.getElementById('idx').scrollTop
         console.log(container,'11111')
    },
    navshow:function(){
    	 var data = this.collapse;
    	 console.log(data)
    	 if(this.collapse){
    	 	this.collapse = false
    	 }else{
    	 	this.collapse = true
       }
       console.log(this.collapse)
    },
    login () {
      this.$router.push('/login')
    },
    handleRegister () {
      this.$router.push({ name: 'register' })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang='stylus'>
/*.navwrap
  width 100%
.nav
  display:flex
  height:75px
  align-items:center
  justify-content space-between
  padding 0 100px
  font-size 15px
  .logowrap
    img
      width: 139px
      height: 42px
.el-menu
  display flex
  justify-content space-between
  border-bottom none
  background-color transparent

.el-menu-item.is-active
  color #409EFF!important
  border-bottom 1.5px solid #409EFF !important
.el-menu-item
  height 45px !important
  line-height 45px !important
  padding 0 0 !important
  margin 0 60px
  color #323232 !important
  font-size 18px !important
  background-color transparent !important
.el-button--primary
  background-color #409EFF
  border-color #409EFF
  color white
.el-button--primary:hover
  background-color #f9f9f9
  color #409EFF
.el-button--default
  background-color transparent
  border-color #323232
  color #323232
.el-button--default:hover
  background-color #f9f9f9
  color #409EFF
  border-color #409EFF
.el-button
  padding 5px 15px
  font-size 18px
  margin-left 30px
.buttons
  display flex
  justify-content space-between*/

</style>

<style lang="stylus" scoped>
	.nav .active{
		display: block;
	}
	.navwrap{
		width: 100%;
		background: #FFFFFF;
		border-bottom: solid 1px #e6e6e6;;
	}

	.nav{
		width: 1200px;
		margin: 0 auto;
		position: relative;
		padding-top: 10px;
	}

	.nav:after{
		content: "";
		display: table;
		clear: both;
		height: 0;
	}

	.logowrap{
		width: 100px;
		float: left;
	}

	.logowrap img{
		width: 100%;
	}

	.navph{
		float: left;
		width: 1080px;
	}

	.navph:after{
		content: "";
		display: table;
		clear: both;
		height: 0;
	}

	.tabs {
		float: left;
		padding:0 50px;
		box-sizing: border-box;
		-webkit-box-sizing: border-box;
		-moz-box-sizing: border-box;

	}

	.el-menu-item{
		font-size: 18px;
	}

.el-menu--horizontal>.el-menu-item{
	line-height: 40px;
}

.el-menu.el-menu--horizontal{
	border-bottom: none ;
}

	.tabs ul li{
		padding: 0 40px;
		line-height: 40px;
		text-align: center;
	}

	.el-menu--horizontal>.el-menu-item{
		height: auto;
	}

	.buttons{
		float: right;
	}


	.el-menu-item.is-active,.el-menu--horizontal>.el-menu-item {
		border-bottom:none !important;
	}

	.el-menu-item.is-active:hover {
		border-bottom:none  !important;
	}

	.el-menu-item span {
		display: inline-block;
		height: 40xpx;
	}

	.el-menu-item.is-active span {
		border-bottom: 1.5px solid #409eff;
	}

	.el-menu-item span:hover {
		border-bottom: 1.5px solid #409eff !important;
	}

	.contact {
		height: auto;
	}

	.contact {
		padding: 0;
	}

	.contact .contact_text {
		width: 1200px;
		margin: 0 auto;
		top: auto;
		padding: 50px 0;
	}

	.navhide {
		cursor: pointer;
		padding: 10px 0;
		display: none;
		width: 30px;
		border-bottom: 2px solid #e6e6e6;
		height: 2px;
		position: absolute;
		right: 20px;

	}

	.navhide:after {
		content: "";
		height: 2px;
		width: 30px;
		background: #e6e6e6;
		position: absolute;
		top: 10px;
		right: 0;
	}

	.navhide:before {
		content: "";
		height: 2px;
		width: 30px;
		background: #e6e6e6;
		position: absolute;
		top: 0px;
		right: 0;
	}

	@media (max-width: 1200px) {
		.nav {
			width: 100%;
			padding: 10px 20px 0;
		}

		.navph{
			width: 80%;
		}
		.tabs ul li{
			padding: 0 20px;
		}

		.contact .contact_text {
			width: 100%;
			padding: 50px 20px;
		}

		.banfun .banner .banner_left .left_content{
			margin: 50px 0;
			text-align: center;

		}

		.banfun .banner .banner_left{
			width: 100%;
			float: none;
			margin: 0;
		}

		.banfun .banner .banner_right{
			width: 100%;
			float: none;
		}

		.banfun .banner .banner_right img{
			margin: 0 auto;
		}

		.banfun .banner{
			height: auto;
		}

		.function{
			margin-top: 50px;
			padding: 0;
		}

		.function .function_title{
			text-align: center;
		}

		.function .function_images .contents_left{
			width: 33%;
			position: inherit;
			top: auto;
			height: auto;

		}

		.function .function_images .contents_middle{
			position: initial;
			top: auto;
			width: 33%;
			height: auto;
		}

		.function .function_images .contents-content{
			width: 33%;
			height: auto;
			position: initial;
			top: none;
			left: none;
			right: none;
			float: left;
		}

		.function .function_images .contents_right{
			position: initial;
			width: 33%;
			height: auto;
		}

		.function .function_images .contents-content img,.function .function_images .contents_left img,.function .function_images .contents_right img{
			width: 100%;
			height: auto;
		}

		.function .function_images .contents_middle img{
			width: 100%;
			height: auto;
		}

		.function .function_images{
			height: auto;
			padding:0 20px;
		}

		.function .function_images:after{
			display: table;
			content: "";
			clear: both;
		}

		.advan .advan_title{
			position: initial;
			width: 100%;
			padding: 50px 0;
		}

		.advan{
			text-align: center;
		}

		.advan_left,.advan_right{
			display: inline-block;
			width: 321px;
			vertical-align: top;
			margin-bottom: 30px;
		}
		#advan_left_top{
			text-align: center;
		}

		.advan .advan_left img,.advan .advan_right,.advan .advan_left #advan_left_top,.advan .advan_left #advan_left_bottom{
			position: initial;
		}

		.advan .advan_right{
			margin-left: 30px;
		}
		.advan .advan_right img,.advan .advan_left img{
			padding-bottom: 30px;
			height: auto;
			width: 100%;
		}

		.advan .advan_right #advan_right_top{
			margin: 0;
			text-align: center;
			line-height: auto;
			width: 100%;
			height: auto;
		}

		.advan .advan_right #advan_right_bottom{
			height: auto;
			width: auto;
			margin: 0;
			top: 0;
			line-height: auto;
		}

		.advan,.banfun{
			height: auto;
		}
		.advan .advan_right{
			margin-bottom: 30px;
		}

		.advan_flow .advantages{
			height: auto;
		}

		.advan_flow .advantages .plat_advan{
			width: 100%;
			position: initial;
			text-align: center;
			padding: 50px 0;
		}

		.advan2-content{
			width: 100%;
		}

		.advan_flow .advantages img,
		.advan_flow .advantages img,
		.advan_flow .advantages .text1,
		.advan_flow .advantages .text3,
		.advan_flow .advantages .text2{
			position: static;
			margin: 0 auto;

		}

		.advan_flow .advantages .text1,
		.advan_flow .advantages .text3,
		.advan_flow .advantages .text2{
			width: 100%;
			text-align: center;
			right: static;
			margin-top: 10px;
		}
		.advan_flow .flow .flow_title{
			display: block;
			width: 100%;
			text-align: center;
			position: static;
			padding: 50px 0 ;
		}

		.advan_flow .flow{
			padding-bottom: 50px;
		}

		.flow:after{
			content: "";
			display: table;
			clear: both;

		}

		.advan_flow .flow{
			height: auto;

		}

			.advan_flow .flow #flow_left,
			.advan_flow .flow #flow_middle,
			.advan_flow .flow #flow_right,
			.advan_flow .flow .flow_left_text,
			.advan_flow .flow .flow_middle_text,
			.advan_flow .flow .flow_right_text{
				position: initial;
				width: 100%;
			}
			.advan_flow .flow .flow_left_text,
			.advan_flow .flow .flow_middle_text,
			.advan_flow .flow .flow_right_text{
				position: absolute;
				top: 160px;
				left: 0px;
				padding: 0 10px;
				font-size: 12px;
				height: auto;
			}

		.flow-content{
			position: relative;
			width: 30%;
			float: left;
			margin-left: 3.333%;
		}

		.flow-content:after{
			margin-left: 0;
		}

		.advan_flow{
			height: auto;
		}
		.advan_flow .flow .flow_middle_text .flow_middle_span,
		.advan_flow .flow .flow_middle_text,
		.advan_flow .flow .flow_left_text .flow_left_span,
		.advan_flow .flow .flow_right_text .flow_right_span{
			display: block;
			width: 100%;
			font-size: 12px;
			height: 29.6px;
			height: auto;
		}

		.advan_flow .flow .flow_middle_text .flow_middle_span{
			margin: 0;
		}

	}

	@media (max-width: 760px) {
	.flow-content{
		width: 75%;
		margin: 0 auto;
		float: none;
	}
		.nav .active{
		display: none;
	}

	.navph{
		position: absolute;
		width: 100%;
		left: 0;
		background: rgba(0,0,0,.5);
		z-index: 2;
		top: 45px;
	}

	.buttons{
		float: none
	}


	.el-menu.el-menu--horizontal{
		background: none;
	}

	.tabs{
		float: none;
		display: block;
		width: 100%;
		padding: 0;
	}

	.el-menu-item.is-active, .el-menu--horizontal>.el-menu-item{
		width: 100%;
		background: none;
		color: #FFFFFF;
	}

	.el-button--primary{
		width: 100%;
	}
	.el-button+.el-button{
		width: 100%;
		margin-left: 0;

	}

	.el-button{
		border-radius: 0;
	}
		.nav{
			padding-bottom: 10px !important;
		}

		.navhide {
			display: block;
		}

		.contact .contact_text {
			display: block;
		}
		.nav .logowrap img {
			width: 80px !important;
		}

		.tabs {
			display: inline-block;
		}
		.el-menu-item,
		.el-button {
			font-size: 16px !important;
		}
		.contact .contact_text .open_flat {
			margin-top: 20px;
		}
		.contact .contact_text .contact_ways,
		.contact .contact_text .open_flat,
		.contact .contact_text .discuss {
			font-size: 16px;
		}
		.contact .contact_text .open_flat img,
		.contact .contact_text .discuss img {
			display: inline;
		}
		.contact .contact_text .open_flat img {
			margin-bottom: 20px;
		}
		.contact .contact_text .discuss img {
			margin-left: 0px;
		}
		.contact .contact_text .discuss {
			width: 100%;
		}

		.function .function_images .contents_left,
		.function .function_images .contents_middle,
		.function .function_images .contents-content,
		.function .function_images .contents_right{
			margin: 20px auto 0;
			width:70%;
			float: none;
		}

	.banfun .banner .banner_right img{
			width: 90%;

			height: auto;
		}

		.advan_flow .advantages .plat_advan,
		.advan .advan_title,
		.function .function_title,
		.advan_flow .flow .flow_title,
		.banfun .banner .banner_left .left_content .l_c_on{
			font-size: 18px;
		}

		.banfun .banner .banner_left .left_content .l_c_on #l_c_on_ido{
			font-size: 30px;
		}

		.banfun .banner .banner_left .left_content .l_c_on #l_c_on_idt{
			font-size: 24px;
		}
		.banfun .banner .banner_left .left_content .l_c_th #l_c_th_id{
			font-size: 15px;
		}

	}
</style>
