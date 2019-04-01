##Vue.js  
 	中文官网地址: https://cn.vuejs.org/
##是什么
	框架 > 库(jquery)
	渐进式JavaScript前端框架
		HTML+CSS+JavaScript+浏览器 

	渐进式: 
		vue及其生态系统为开发者提供的功能很全面,
		当我们使用vue的时候,我们可以把它当jquery使用,
		dom操作,也可以将vue全家桶当做Reactjs使用,
		视图渲染+路由跳转+状态管理 来开发中大型项目,

		一句话: 
			vue主张最少,利于与其它库或者框架配合使用,
			来开发中大型项目,就叫渐进式 
	作者: 
		中国江苏人  尤雨溪    
		英文名 Evan You     尤小右 


##核心思想
	1.数据驱动
		数据驱动视图

		启发: 
			vue开发项目,对于我们开发者来说 主要关注点在于数据层

		解放了dom操作  --> vue很不提倡dom操作 

	数据变了  -->  驱动 -->  视图的更新 

	解放了dom操作 
		dom操作
			选元素  --->
						属性操作
						样式操作 
						节点操作 
						事件
						动画 

	数据绑定  配合  指令
	应用于数据交互频繁的时候 更多时候用Vue/React

2.组件化 
	vue允许我们把大的页面 拆分 成 一个个的小块(小型页面)

		零件(部件): 组装

	概念: 站在UI角度的来看,将一个大型页面通过拆分(化大为小,化繁为简)的思想,
	      然后单独的去实现某一个小块的功能,最后将这是小块通过特定的方式的
	      去组装在一起,大的页面的就出来了,我们把这些小块视为一个个组件

	本质: HTML + CSS + JS  一个独立的小型页面(视图)
		  在Vue中,就是一个自定义标签

	分类:  全局组件  和 局部组件

	定义: 

		(1). 全局组件: 在每个vue实例中都可以调用
				a.定义: 
				  Vue.component('组件名',{
				  	// 组件的配置 
				  		template: '写组件自己的html结构'
				  });

				  注意: 
				  	(1).组件名不要与html(5)内置标签重名
				  	(2).如果组件定义时名字是驼峰命名,在调用的时候
				  	    需要把名字改成烤串式,组件调用的时候名字一律小写
				  	(3).

				b. 调用组件

			组件作用域:
				每个组件的数据都是一个独立的作用域,
				该组件的数据只能在该其内部使用,
				不能跨组件,如果想把数据传递给其它组件,
				就需要借助组件通信机制

			组件通信: 
				1.父组件 --> 子组件  
					<div id="app">
						<子组件 :key='value' :key2='value2'>
						</子组件>
					</div>	


					在父组件中,通过属性传递给子组件,
					子组件用props接收

					props: {
						key: {
							/* type: 期望的数据类型, */
							type: 单一的类型 || [类型1,类型2,...],
							required: 布尔值,// 是否必传
							default: 默认值 //  不传就走默认值

							/*
								default:  默认值, // 基本类型
								default() {      // 引用类型
									return 默认值;
								}
							*/
						}
					}
					
				2. 子组件  --> 父组件 
					给子组件添加一个ref='名字'

					在父组件中
						this.$refs.名字

					ref: 既可以组件也可以获取原生dom元素

						1.如果ref添加组件上,this.$refs.名字, 拿到的就是组件

						2.如果ref添加在普通标签上,this.$refs.名字,拿到的就是原生dom元素

		(2). 局部组件

##为什么目前很火	
	目前前端的三大主流框架 


	angular    Google的后台工程师开发并维护 

    react      Facebook的两名前端工程师开发并维护 

	vue       尤雨溪个人开发并维护 


	vue = react精华(虚拟DOM,组件化) + angular精华(指令，双向数据绑定）

	vue特点: 
		1.简单易学
		2.灵活(vue全家桶 = vuejs + vue-router + vuex)
		3.高效(超快的虚拟DOM)



##使用
	1.下载  得有vuejs框架 
		(1).cdn
		(2).源码下载到本地
		(3).npm/cnpm 
	2.将vuejs引入到html文件
	<script src='node_modules/vue/dist/vue.js'></script>

	3.使用
		当我们把vue框架引入之后,框架会暴露
		一个名字叫Vue的构造函数,
		接下来就可以使用Vue构造函数来做事了


		<div id="box">
			<p>{{key}}</p>
			<p>{{key2}}</p>
			<p>{{key3}}</p>
		</div>	


		new Vue({
			el: '#box',// 推荐传id,不能传body或html标签
			data: {
				key:  value,
				key2: value2,
				key3: value3
			}
		})


	{{ xxx }}: 插值符号 
		1.属性名   
		2.表达式   算术运算，三目运算 
		3.调用方法


		注意: 不能放语句块(定义变量、if、for、function(){}),
		不能出现标签的属性中 例如title='{{a}}'


##指令  directive

	概念: 
		在vue中,指令都是以v-开头,
		指令是直接在标签身上使用的,
		也就是指令扩展了标签的功能

	v-bind:属性名='数据'                绑定属性  
	简写:      :属性名='数据'  能简写的就简写

	v-on:事件名='函数' 
		简写: @事件名='函数' 

		注意: 事件名不带on   v-on:mouseenter='fn'
	支持传参数

    v-show和v-if：
        1.给人的视觉效果一样，看上去都是让元素显示和隐藏
        2.v-show是通过控制元素的display属性
          v-if是通过控制DOM节点的移除和插入，实现元素的条件渲染

          条件渲染：
            是否在文档中，条件成立，在文档中，条件不成立，就不再文档中。

    v-if=''和v-else-if=''和v-else三个中，每次只显示一个。

    v-for循环：列表渲染

        v-for='item,index in navs' :key='index'
            循环数字，数组，字符串
                item    ：代表循环的每一项
                index   ：每一项的下标
                in      ：关键字
                navs    ：data里的数组的键
                :key    ：可以加快页面的渲染速度



        v-for='value,key,index in navs' :key='index'
            循环对象
                value   ：代表循环的每一个键的值
                key     ：每一个键
                index   ：索引
                in      ：关键字
                navs    ：data里的数组的键
                :key    ：可以加快页面的渲染速度


v-model		：等号后面不能跟表达式
	<input input='text' v-model='a'>
	<p>{{a}}</p>

	在input中输入，p的内容夜壶跟着改变
	修饰符：
		lazy		由原来的input事件转换为change事件
						当文本框失去焦点的时候，触发数据的改变
			<input input='text' v-model.lazy='a'>
			<p>{{a}}</p>

		number		尽量的将文本框的value值，往数字的方向转，不能转的就保持原来的样子
			<input input='text' v-model.number='a'>
			<p>{{a}}</p>

		trim		去掉首尾的空格


v-text			不解析标签
v-html			可以解析标签
		都是将原来的内容清除之后，在放东西


优化：
	v-pre		：禁用双大括号，告诉vue不解析{}，把它当作普通文本对待	<p v-pre>{{a}}</p>		显示{{a}}

	v-once		：只绑定一次，第一次渲染他，后续数据变了，这个dom不更新了

	v-cloak		：隐藏{{}}，当数据加载完毕，v-cloak会自动从元素身上移除







class
	1.对象绑定
		:class='{类名1:数据1(布尔值),类名2:数据2(布尔值),类名3:数据3(布尔值),...}'

		如果类名对应的值是true,该类就会添加到元素上,否则不添加

	2.数组绑定 	
		:class='[数据1,数据2,...]'

		data:{
			数据1: 类名1,
			数据2: 类名2,
			...
		}

	3.数组配合对象
		:class='[{类名:数据1(布尔值)},数据2]'

		data: {
			数据1: 布尔值,
			数据2: 类名
		}



style


###计算属性(computed)
	定义: 对data中数据进一步加工处理,在这个数据的基础上计算出
	另一个结果,这个数据称为该计算属性的依赖

	{{}} 插值符号
	本意只是用来盛放 普通的属性或表达式 或 调用方法(一个)
	不推荐在{{}} 写过于复杂的式子,违背了{{}} 本意,
	当我们需要对data中的数据做进一步加工(处理)的话,推荐使用计算属性  
	特点:
		1.声明的时候是函数,调用的时候的是属性,调用的时候不能加括号() 
		
		2.计算属性的结果是通过return返回出去的,也就是说return什么,今后计算属性就渲染成什么,如果不return,计算属性就不渲染,计算属性必须return 
		
		3.只要计算属性的依赖发生变化,那么这个计算属性都会重新执行一次,得出最新的结果

		4.计算属性有缓存(缓存是个临时存储数据的一个空间/容器),也就是说如果多次使用同一个计算属性,并且该计算属性的依赖如果没有发生变化,那么第一次计算属性的结果会被缓存下来,今后(第二次及其以后)在调用这个计算属性的时候,不会再去执行计算属性的函数,而是直接从缓存取出

		5.不能进行异步操作,只能进行同步操作 

		6.计算属性可以依赖多个data中的数据得出一个结果 
		只要计算属性的某个依赖发生变化,那么这个计算属性都会重新执行一次,得出最新的结果


##watch
	监听 
	用来监视data中的声明的数据 
	由于数据类型有基本类型和引用类用
	vue对它们有所不同

	(1)对于基本类型来说,只要它的值改变了,vue就认为它变了,
	   所以我们可以直接监视

	(2)对于引用类型
		a.键值对这种对象,如果我们只是改变了这个的属性值的话,
		  由于其内存地址没变,这时vue认为这个对象没有变,所以
		  监视不到,但是有些时候,我们修改了对象的属性值,也想 让vue帮助我们监视这个对象,那么就需要深度监视

		b.数组,使用(1)这种方式监视,也可以采用(2),但是不推荐
		  用深度监视,因为深度监视工作量较大,耗性能,所以咱们
		  采用直接监视的方法

	用途: 
		异步操作或一些开销较大的工作(例如DOM操作)

```
	data: {
		a: 1,
		obj: {
			name: 'xxx',
			age: 18
		}
	},
	watch: {
		// 直接监视 
		a(newVal,oldVal) {
			console.log(this);// vm
		},

		// 深度监视 
		obj: {
			deep: true,
			handler(newVal) {
				console.log(this);// vm
			}
		}

	}
```

computed
	1.有缓存
	2.只适合同步操作
	3.依赖data中的数据得到一个新的结果 

	对data中的数据进一步加工 

methods

	普通方法
	调用一次,执行一次 


键盘事件
	onkeydown
	onkeyup
	onkeypress


	按键修饰符

		enter   回车键
		esc     退出键
		space   空格键

## 生命周期 

	vue实例(所有的组件)从 出生 到 销毁 经历的历程

	在不同的阶段,vue会自动执行一些函数,这些函数就称为vue
	的生命周期,这也就给我们开发者提供了编写自己的代码的时机 
	生命周期官方也称为(生命周期)钩子函数

	4个阶段,8个钩子 

		创建 
			创建前   
				beforeCreate  
				特点: 
					无法操作data中的数据,无法dom操作
					
			创建后   
				created
				特点: 
					可以操作data中的数据,但无法dom操作
					适合发请求

		挂载
			
			挂载前: beforeMount
					vue还没开始做事,没有解析{{}},计算属性,没有解析指令等等
			挂载后: mounted
					vue已经做事了,该解析的解析,该替换的替换
					适合dom操作

		更新: 初次渲染  钩子不会执行,
			更新是伴随数据的改变而触发的,
			当数据变了,视图要变,就会触发更新的钩子  

			只要数据变了,就会触发这两个钩子
			
			更新前: beforeUpdate

			更新后: updated

		销毁: 让vue停止工作
			销毁前: beforeDestroy 
			销毁后: destroyed
				适合做组件优化，如如关闭定时器，移除事件监听器......

			两种方式: 
				1. vue实例的$destroy方法  

				2. v-if指令 




###内置的组件
		component
				用来盛放动态组件
				通过is属性切换组件
				<component :is='组件名'></component>

		transition
				<transition name='xxx'></transition>
				两个阶段(进入，离开)
				六个状态	
						进入时			.xxx-enter	{进入动画的初始样式}
						进入中			.xxx-enter-active		{}
						进入结束		.xxx-enter-to

						离开时			.xxx-leave
						离开中			.xxx-leave-active
						离开结束		.xxx-leave-to

		transition-group与transition都是vue的内置组件，用于给元素或组件添加动画的，动画的实现方式借助的都是CSS3的动画，
			支持transition和animation两种动画
		区别：
			transition：作用单个元素或单个组件
			transition-group：作用多个元素和多个组件

		用法：
			二者用法一致

			<transition name='xxx'>
					<标签></标签>
					或
					<组件></组件>
			</transition>


		keep-alive
				当一个组件被频繁的销毁或创建的时候，很消耗计算机性能的，因为需要频繁的创建和删除节点，为了避免这种消耗，我们可以使用keep-alive包裹该组件，这样不会被频繁的创建或销毁，而是让该组件一直或者，只是处于停用和激活状态

				组件一旦被keep-alive包裹着，就不会触发deforeDestory和destoryed钩子了，而会触发activated和deactivated着两个钩子

				activated：组件激活时触发
				deactivated：组件停用时触发

				组件的停用与激活
						<keep-alive></keep-alive>
		slot
	
### 动画

### 过滤器 / 自定义指令 

### axios

### vue-router 

### vuex
