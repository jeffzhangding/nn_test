<template>
	<view class="content">		
		<!-- <button  @click="getAction">test</button> -->
		<view class="search">
			<input :value="inputKeys" maxlength="200" class="search_input" @blur="inputSearchKeys" @focus="clearSearchKeys()"/>
			<button  @click="searchKeys" style="display: flex;align-items: center;">搜索</button>
		</view>
		
		<view class="check_box_div">
			<view class="label_front">常用核查网站:</view>
			<view>
				<checkbox-group class="check_box_p" @change="checkboxChange">			
					<label>
						<checkbox value="wusong" style="transform:scale(0.7)" /> 无讼
					</label>
					<label>
						<checkbox value="faxin" style="transform:scale(0.7)" /> 法信
					</label>
					<label>
						<checkbox value="caipan" style="transform:scale(0.7)" /> 裁判文书网
					</label>
					<label>
						<checkbox value="fabao" style="transform:scale(0.7)" /> 北大法宝
					</label>
				</checkbox-group>
			</view>
		
			<view class="label_front">查询企业信息类网站:</view>
			
			<view>
				<checkbox-group class="check_box_p" @change="checkboxChange2">
								
					<label>
						<checkbox value="xinxigongshi" style="transform:scale(0.7)" /> 信息公示系统
					</label>
					<label>
						<checkbox value="zhixingxinxi" style="transform:scale(0.7)" /> 中国执行信息公开网
					</label>
					<label>
						<checkbox value="xinyongzhongguo" style="transform:scale(0.7)" /> 信用中国
					</label>
					<label>
						<checkbox value="shshuiwuju" style="transform:scale(0.7)" /> 上海市税务局
					</label>
					<label>
						<checkbox value="zqtouzi" style="transform:scale(0.7)" /> 证券投资基金业协会
					</label>
					<label>
						<checkbox value="zqjiaoyisuo" style="transform:scale(0.7)" /> 上海证券交易所
					</label>
					<label>
						<checkbox value="sjsuo" style="transform:scale(0.7)" /> 深圳交易所
					</label>
					<label>
						<checkbox value="qichacha" style="transform:scale(0.7)" /> 企查查
					</label>
					<label>
						<checkbox value="tianyancha" style="transform:scale(0.7)" /> 天眼查
					</label>
				</checkbox-group>
			</view>
		</view>
		<!-- <view style="flex-grow: 1;"></view> -->
		
	</view>
	
</template>

<script>
	export default {
		data() {
			
			return {
				title: 'Hello',
				openWebItem: [],
				openWebItem2: [],
				inputKeys: '请输入您要搜索的内容',
				first_input: true,
				urlObj: {
					wusong: function(keys) {
						var key_list = keys.split(' ')
						var i
						var u1='https://www.itslaw.com/search?searchMode=judgements&sortType=1&searchView=text'
						for (i=0; i<key_list.length; i++) {
							u1 = u1 + '&conditions=searchWord%2B'+key_list[i]+'%2B1%2B'+key_list[i]
						}
						return u1
					},
					faxin: function(keys) {
						var url = 'http://www.faxin.cn/alllibsearch/SearchResult.aspx';
						var para = [
							['keyword', keys],
							['IsInResult', 0],
							['keyword_inResult', null],
							['usersearchtype', 5],
							['rdo_search_tj', 3],
							['rdo_search_fs', 'a'],
							['WebUCSearch1$hiddkeyword', null],
							['WebUCSearch1$hiddIsResultWord', keys],
							['hiddusersearchtype', null],
							['zyflsearchtype', 1],
							['keywordlistnum', 30],
							['zyfl_sort', null],
							['zyfltjlistnum', 30],
							['zyflsort', 1],
							['dffltjlistnum', 30],
							['dfflsort', 1],
							['alyz_sort', null],
							['alyztjlistnum', 30],
							['alyzsort', 1],
							['syyl_sort', null],
							['syyltjlistnum', 30],
							['syylsort', 1],
							['flwx_sort', null],
							['flwxtjlistnum', 30],
							['flwxsort', 1],
							['fltstjlistnum', 30],
							['fltssort', 1]
						];
					postOpenWindow(url, para)
					
					},
					caipan: function(keys) {
						var pageId = uuid()
						return 'http://wenshu.court.gov.cn/website/wenshu/181217BMTKHNT2W0/index.html?s21='+keys+'&pageId='+pageId
					},
					fabao: function(keys) {
						// var url = 'http://www.pkulaw.cn/doSearch.ashx'
						// var para = [
						// 	['keyword', keys],
						// 	['range', 'name'],
						// 	['Search_Mode', 'accurate'],
						// 	['menu_item', 'law'],
						// 	['Db', 'chl,protocol,lawexplanation,whitebook,workreport,introduction'],
						// 	[null, null],
						// 	['nomap', null],
						// 	['EncodingName', null],
						// 	['time', 0.9868864750309034]
						// ];
						// postOpenWindow(url, para)
						var d;
						d = window.open('http://www.pkulaw.cn/')
					},
					xinxigongshi: function(keys) {return 'http://www.gsxt.gov.cn/index.html' },
					zhixingxinxi: function(keys) {return 'http://zxgk.court.gov.cn/zhzxgk/'},
					xinyongzhongguo: function(keys) {
						return "https://www.creditchina.gov.cn/xinyongxinxi/index.html?index=0&scenes=defaultScenario&tableName=credit_xyzx_tyshxydm&searchState=2&entityType=1,4,5,6,7,8&keyword="+keys
					},
					shshuiwuju: function(keys) {return "http://www.tax.sh.gov.cn/newxbwz/wzfw/YhscxCtrl-yhsCx.pfv"},
					zqtouzi: function(keys) {return "http://gs.amac.org.cn/amac-infodisc/res/pof/manager/index.html"},
					zqjiaoyisuo: function(keys) {return "http://www.sse.com.cn/home/search/?webswd="+keys},
					sjsuo: function(keys) {return "http://www.szse.cn/application/search/index.html?keyword="+keys},
					qichacha: function(keys) {return "https://www.qichacha.com/search?key="+keys},
					tianyancha: function(keys) {return "https://www.tianyancha.com/search?key="+keys}
				}
			}
		},
		onLoad() {

		},
		methods: {
			checkboxChange: function (e) {
    //             console.log(e)
				// console.log(this.openWebItem)
			    this.openWebItem = e.detail.value
			},
			
			checkboxChange2: function (e) {
			//             console.log(e)
						// console.log(this.openWebItem)
					    this.openWebItem2 = e.detail.value
			},
			
			searchKeys: function () {
				var i;
				// console.log(this.openWebItem.length)
				var l = [];
				l = l.concat(this.openWebItem).concat(this.openWebItem2)
				for (i=0; i<l.length; i++) {
					var v = l[i]
					var openUrl = null
					// console.log(this.urlObj)
					if (this.urlObj[v] != null) {
						openUrl = this.urlObj[v](this.inputKeys)
						if (openUrl) {
							window.open(openUrl);
						}
					}
					
				}
				
			},
			inputSearchKeys: function(e) {
				// console.log(this.inputKeys)
				this.inputKeys = e.detail.value
			},
			clearSearchKeys: function() {
				if (this.first_input) {
                   this.inputKeys = ''
				   this.first_input = false
                }
			},
			
		},
		
	}
	
	/*
	*功能： 模拟form表单的提交
	*参数： URL 跳转地址 PARAMTERS 参数
	*/
	function postOpenWindow(URL, PARAMTERS) {
		//创建form表单
		var temp_form = document.createElement("form");
		var i = 0;
		
		temp_form.action = URL;
		temp_form.target = "_blank";
		temp_form.method = "post";
		temp_form.style.display = "none";
		for (i=0; i < PARAMTERS.length; i++) {
			var opt = document.createElement("textarea");
			opt.name = PARAMTERS[i][0];
			opt.value = PARAMTERS[i][1];
			temp_form.appendChild(opt);
		}
		document.body.appendChild(temp_form);
		temp_form.submit()
	};
	
	function uuid() {
	    var s = [];
	    var hexDigits = "0123456789abcdef";
	    for (var i = 0; i < 36; i++) {
	        s[i] = hexDigits.substr(Math.floor(Math.random() * 0x10), 1);
	    }
	    s[14] = "4";  // bits 12-15 of the time_hi_and_version field to 0010
	    s[19] = hexDigits.substr((s[19] & 0x3) | 0x8, 1);  // bits 6-7 of the clock_seq_hi_and_reserved to 01
	    s[8] = s[13] = s[18] = s[23] = "-";
	 
	    var uuid = s.join("");
	    return uuid;
	}
</script>

<style>

	.content {
		display: flex;
		flex-direction: column;
		background-color: #333333;
		color: #C8C7CC;
		/* background-size: cover; */
		/* flex-grow: 1; */
		height: 400rpx;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
	
	.search {
		display: flex;
		flex-direction: row;
		margin-top: 60rpx;
		align-self: center;
		justify-content: center;
	}
	
	.search_input {
		outline-style: none ;
		border: 1px solid #ccc; 
		border-radius: 3px;
		padding: 6rpx;
		width: 620px;
		font-size: 24px;
	}
	
	.check_box_p {
		font-size: 5rpx;
		display: flex;
		/* align-items: flex-start; */
		flex-direction: column;
	}
	.label_front {
		font-size: 8rpx;
		margin-top: 15rpx;
	}
	.check_box_div {
		display: flex;
		flex-direction: column;
		justify-content: flex-start;
		align-items: flex-start;
		
		position: relative;
		/* left: 200rpx; */
		margin-left: 270rpx;
		margin-right: 150rpx;
		flex-wrap: wrap;
		/* width: 1000rpx; */
		/* margin: 100rpx; */
	}
	
	
</style>
