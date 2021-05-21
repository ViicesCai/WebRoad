# Vue入门学习

> `vue.js`是一套构建用户界面(UI)的渐进式`JavaScript`框架

## 简介

+ `JavaScript`框架
+ 简化`Dom`操作
+ 响应式数据驱动

### MVVM

> M/V/VM
>
> `M`：`model`数据模型；`V`：`view`视图；`VM`：`ViewModel`视图模型

![img](https://www.ruanyifeng.com/blogimg/asset/2015/bg2015020110.png)

+ `MVVM`通过数据双向绑定让数据自动地双向同步
  + `V（修改数据） -> M`
  + `M（修改数据） -> V`
  + 数据是核心

## 第一个Vue程序

> 学习`Vue`要转化思想：不要在想着怎么操作`DOM`，而是想着如何操作数据

``` html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
	</head>
	<body>
        <!-- 渲染数据 -->
		<div id="app">
			{{message}}
		</div>
		
		<!-- 导入Vue.js -->
		<script src="vue.js"></script>
		<script>
            // 创建vue对象，设置 el 和 data 属性
			var vm = new Vue({
				el: "#app",
				data: {
					message: "HelloWorld"
				}
			});
            // 在js中可以通过 vm.$data.message 或 vm.message 来访问到一个vue实例中的值
		</script>
	</body>
</html>
```

## 基础知识

### 数据绑定

> 我们可以通过`{{}}`从数据对象中获取值，可以看成是一个虚拟的`DOM`

+ 数据对象的属性值发生改变，`{{}}`的内容也会更新
+ `{{}}`中只能出现`JavaScript`表达式而不能解析`js`语句
+ **不能作用在 HTML 元素的属性上**

``` html
<h1>Hello, {{ msg }}.</h1>
<p>{{ 1 + 2 }}</p>
<p>{{ isOk ? 'yes': 'no' }}</p>

<!-- ！！！错误示范！！！ -->
<h1 title="{{ err }}"></h1>
```

### 双向数据绑定

> 将`DOM`与`Vue`实例的`data`数据绑定到一起，彼此之间相互影响
>
> 之后的`v-model`就可以实现数据绑定

+ 数据的改变会引起`DOM`的改变
+ `DOM`的改变也会引起数据的变化

#### 动态添加数据的注意点

+ 只`data`中的数据才是响应式的，动态添加进来的数据默认为非响应式

### el：挂载点

> 与HTML的标签进行绑定

#### 选择器

> 只支持双标签，不支持单标签，且：不能挂在到`HTML`和`Body`上，推荐使用`div`进行挂载

+ `el:"#id名"`：通过`id`进行选择：推荐
+ `el:".class名"`：通过`class`进行选择
+ `el:"div"`：通过标签进行选择

### data：数据对象

+ `Vue`中用到的数据定义在`data`中
+ `data`中可以写复杂类型的数据
+ 渲染复杂类型的数据时，遵守`js`的语法

``` html
<div id="app">
    渲染简单数据：{{ message }} <br>
    渲染复杂数据：{{ student.name }} <br>
    渲染数组：{{ schools[1] }} <br>
</div>

<script src="vue.js"></script>
<script>
    var app = new Vue({
		el: "#app",
		data: {
			message: "学生信息",
			student: {
				name: "CAI",
				age: "21",
				sex: "男"
            },
			schools:["师大附中", "至诚学院"]
        }
    });
</script>
```

### 指令

> 指令 `(Directives)`是带有 `v-` 前缀的特殊属性
>
> 当表达式的值改变时，将其产生的连带影响，响应式地作用于`DOM`

#### v-text

> 设置标签的文本值`(textContent)`

+ 默认写法会替代标签的全部内容，使用差值表达式`{{}}`可以替换指定内容
+ 内部支持表达式

``` html
<div id="app">
	<h2 v-text="message"></h2>
	<h2 v-text="message+'!'"></h2>
</div>
		
<script src="vue.js"></script>
<script>
	var app = new Vue({
		el: "#app",
		data: {
			message: "HelloWorld"
		}
	});
</script>
```

#### v-html

> 设置标签内的`innerHTML`

+ 内容中有`HTML`结果会被解析为标签
+ `v-text`无论内容是什么，只会被解析为文本

``` html
<div id="app">
	<h2 v-html="content"></h2>
</div>
		
<script src="vue.js"></script>
<script>
	var app = new Vue({
		el: "#app",
		data: {
			content: "<h1>HelloWorld</h1>"
		}
	});
</script>
```

#### v-on

> 为元素绑定事件

+ 事件名不需要写`on`
+ 指令可以简写为`@`
+ 绑定的方法定义在`methods`属性中

``` html
<div id="app">
	<!-- 单击事件 -->
	<input type="button" value="v-on指令" v-on:click="doSomething" />
	<input type="button" value="v-on简写" @click="doSomething" />
			
	<!-- 双击事件 -->
	<input type="button" value="双击" @dblclick="doSomething" />
			
	<!-- 动态修改属性 -->
	<h2 @click="changeData">{{ food }}</h2>
</div>

<script src="vue.js"></script>
<script>
	var app = new Vue({
		el: "#app",
		data: {
			food: "烤鸡翅"
		},
		methods: {
			doSomething: function() {
				alert("doSomething...");
            },
					
			changeData: function() {
				this.food += "真好吃";
			}
		},
	});
</script>
```

##### 事件修饰符

+ `.stop`阻止冒泡，调用 `event.stopPropagation()`
+ `.prevent`阻止默认行为，调用 `event.preventDefault()`
+ `.capture`添加事件侦听器时使用事件捕获模式
+ `.self`只当事件在该元素本身（比如不是子元素）触发时，才会触发事件
+ `.once`事件只触发一次

#### 实现一个计数器

> 结合`v-text v-html v-on`的案例

``` html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>计数器</title>
	</head>
	<body>
		<div id="app">
			<button @click="sub">-</button>
			<span>{{ num }}</span>
			<button @click="add">+</button>
		</div>
		
		<script src="vue.js"></script>
		<script>
			var app = new Vue({
				el: "#app",
				data: {
					num: 1
				},
				methods: {
					add: function() {
						if (this.num < 10) {
							this.num++;
							
						} else{
							alert("已经到顶了");
						}
					},
					
					sub: function() {
						if (this.num > 0) {
							this.num--;
							
						} else{
							alert("已经到底了");
						}
					}
				}
			});
		</script>
	</body>
</html>
```

#### v-show

> 根据表达值的真假，切换元素的显示和隐藏

+ 原理：修改元素的`display`实现显示隐藏
+ 指令后面的内容，最终都会解析为布尔值
+ 值为`true`元素显示，值为`false`元素隐藏

``` html
<div id="app">
	<input type="button" value="切换显示状态" @click="changeShow" />
	<h1 v-show="isShow">显示的数据</h1>
</div>
		
<script src="vue.js"></script>
<script>
	var app = new Vue({
		el: "#app",
		data: {
			isShow: true
		},
		methods: {
			changeShow: function() {
				this.isShow = !this.isShow;
			}
		}
	});
</script>
```

#### v-if

> 根据表达值的真假，切换元素的显示和隐藏（操纵`dom`元素）

+ 本质是通过操纵`dom`元素来切换显示状态
+ 表达式的值为`true`，元素存在于`dom`树中；为`false`，从`dom`树中移除
+ 如果需状态切换频繁的话使用`v-show`消耗较小

``` html
<div id="app">
	<input type="button" value="切换显示" @click="changeShow" />
	<p v-if="isShow">Hello</p>
</div>
		
<script src="vue.js"></script>
<script>
	var app = new Vue({
		el: "#app",
		data: {
			isShow: false
		},
		methods: {
			changeShow: function() {
				this.isShow = !this.isShow;
			}
		}
	});
</script>
```

#### v-bind

> 设置元素的属性：如`(src,title,class)`
>
> 当表达式的值改变时，将其产生的连带影响，响应式地作用于`DOM`

+ `v-bind`:属性名
+ 简写：`:属性名`
+ 需要动态的增删`class`：使用对象方式

``` html
<style>
    .active {
		border: 1px solid red;
	}
</style>
<body>
    <div id="app">
		<img v-bind:src="imgSrc" alt="">
		<br>
		<img :src="imgSrc" alt="" :title="imgTitle+'!!'" :class="isActive?'active':''" @click="active" />
		<br>
        <!-- class的值active，取决于isActive的值 -->
		<img :src="imgSrc" alt="" :title="imgTitle" :class="{active:isActive}" @click="active" />
	</div>
		
	<script src="vue.js"></script>
	<script>
		var app = new Vue({
			el: "#app",
			data: {
				imgSrc: "http://www.itheima.com/images/logo.png",
				imgTitle: "黑马",
				isActive: false
			},
			methods: {
				active: function() {
					this.isActive = !this.isActive;
				}
			}
		});
	</script>
</body>
```

#### v-for

> 根据数据生成列表结构

+ 与数组结合使用
+ `(item, index) in` 数据
+ `item`和`index`可以结合其他指令一起使用
+ 数组长度的更新会同步到页面上，是响应式的

``` html
<div id="app">
	<input type="button" value="添加数据" @click="add" />
	<input type="button" value="移动数据" @click="remove" />
		
	<ui>
		<li v-for="(it, index) in arr">
			{{ index+1 }} 城市：{{ it }}
		</li>
	</ui>
			
	<h2 v-for="student in students" :title="student.name">
		{{ student.name }}
	</h2>
</div>
		
<script src="vue.js"></script>
<script>
	var app = new Vue({
		el: "#app",
		data: {
			arr: ["福州", "泉州", "广州"],
			students: [
				{name: "CAI"},
				{name: "Jack"},
				{name: "Tom"}
			]
		},
		methods: {
			add: function() {
				this.students.push({name: "新同学"});
			},
					
			remove: function() {
				this.students.shift();
			}
		}
	});
</script>
```

##### key属性

> 使用 `v-for` 的时候提供 `key` 属性，以获得性能提升

+ 使用`key`，`VUE`会基于`key`的变化重新排列元素顺序，并且会移除`key`不存在的元素

``` html
<div v-for="item in items" v-bind:key="item.id">
  <!-- 内容 -->
</div>
```

##### 数组操作

- `push()`
- `pop()`
- `shift()`
- `unshift()`
- `splice()`
- `sort()`
- `reverse()`

#### v-model

> 便捷的设置和获取表单元素的值

+ 绑定的数据会和表单元素值相关联
+ 双向数据绑定

``` html
<div id="app">
	<input type="button" value="修改信息" @click="set" />
	<input type="text" v-model="message" @keyup.enter="get" />
	<h2>{{ message }}</h2>
</div>
		
<script src="vue.js"></script>
<script>
	var app = new Vue({
		el: "#app",
		data: {
			message: "Hello"
		},
		methods: {
			get: function() {
				alert(this.message);
			},
					
			set: function() {
				this.message = "Nice day";
			}
		}
	});
</script>
```

### watch：监视数据变化

> `watch`是一个对象，键是需要观察的表达式，值是对应回调函数

+ 当表达式的值发生变化后，会调用对应的回调函数完成响应的监视操作

``` js
new Vue({
  data: { a: 1, b: { age: 10 } },
  watch: {
    a: function(val, oldVal) {
      // val 表示当前值
      // oldVal 表示旧值
      console.log('当前值为：' + val, '旧值为：' + oldVal)
    },

    // 监听对象属性的变化
    b: {
      handler: function (val, oldVal) { /* ... */ },
      // deep : true表示是否监听对象内部属性值的变化 
      deep: true
    },

    // 只监视user对象中age属性的变化
    'user.age': function (val, oldVal) {
    },
  }
})
```

### computed：计算属性

> 计算属性是基于它们的依赖进行缓存的，只有在它的依赖发生改变时才会重新求值

+ `{{}}`中不要放入太多的逻辑，否则会让模板过重、难以理解和维护
+ `computed`中的属性不能与`data`中的属性同名，否则会报错

``` js
var vm = new Vue({
  el: '#app',
  data: {
    firstname: 'jack',
    lastname: 'rose'
  },
  computed: {
    fullname() {
      return this.firstname + '.' + this.lastname
    }
  }
})
```

## 过滤器

> 文本数据格式化

+ 过滤器可以用在两个地方：`{{}}`和`v-bind`表达式
+ 分为：全局过滤器和局部过滤器

### 全局过滤器

> 通过全局方式创建的过滤器，在任何一个`vue`实例中都可以使用

+ 使用全局过滤器的时候，需要先创建全局过滤器，再创建`Vue`实例
+ 显示的内容由过滤器的返回值决定

``` js
Vue.filter('filterName', function (value) {
  // value 表示要过滤的内容
})
```

### 局部过滤器

> 局部过滤器是在某一个`vue`实例的内容创建的，只在当前实例中起作用

``` js
{
  data: {},
  // 通过 filters 属性创建局部过滤器
  // 注意：此处为 filters
  filters: {
    filterName: function(value, format) {}
  }
}
```

## 生命周期

> `Vue`实例有一个完整的生命周期也叫做：组件生命周期
>
> 一个组件从开始到最后消亡所经历的各种状态，就是一个组件的生命周期
>
> 即：从开始创建、初始化数据、编译模板、挂载`Dom`→渲染、更新→渲染、卸载等一系列过程，我们称这是`Vue` 的生命周期

![Vue 实例生命周期](https://cn.vuejs.org/images/lifecycle.png)

| 步骤                                     | 详解                                                         |
| ---------------------------------------- | ------------------------------------------------------------ |
| `new Vue()`                              | 创建`Vue`实例                                                |
| `init events & lifecycle`                | 开始初始化                                                   |
| `beforeCreate`                           | 组件创建之前，此时还没有`data`属性                           |
| `init injections & reactivity`           | 通过依赖注入导入依赖项                                       |
| `created`                                | 组件实例创建完成，属性已绑定（有data属性），`DOM`还未生成（没有el属性） |
| `el`属性                                 | 检查`Vue`配置，查看是否配置了`el`，有则继续检查`template`项  |
| `template`                               | 没有该属性则被绑定区域的`el`对象（如：`<div id="app"></div>`整个`DOM`对象）都被作为被填充对象替换掉填充区域 |
| `beforeMount`                            | 模板编译、挂载前                                             |
| `create vm.$el and replace "el" with it` | 编译，并替换了被绑定元素                                     |
| `mounted`                                | 编译、挂载                                                   |
| `beforeUpdate`                           | 组件更新之前                                                 |
| `update`                                 | 组件更新之后                                                 |
| `destroy`                                | 当`vm.$destroy()`被调用，开始拆卸组件和监听器，生命周期结束  |

### 生命周期钩子

> 从组件被创建，到组件挂载到页面上运行，再到页面关闭组件被卸载，这三个阶段总是伴随着组件各种各样的事件，这些事件，统称为组件的生命周期函数
>
> `Vue`在执行过程中会自动调用生命周期钩子函数，我们只需要提供这些钩子函数即可

1. `beforeCreate()`

   + 在实例初始化之后，数据观测` (data observer)` 和`event/watcher`事件配置之前被调用
   + 此时，`data computed watch methods`上的方法和数据均不能访问
   + 可以在这加个`loading`事件
2. `created()`

   + 实例创建完成
   + 可访问`data computed watch methods`上的方法和数据
   + 未挂载`DOM`,不能访问`el，ref`为空数组
   + 可在这结束`loading`，发送请求获取数据
3. `beforeMounted()`

   + 在挂载开始之前被调用
4. `mounted()`

   + 此时，`vue`实例已经挂载到页面中，可以获取到`el`中的`DOM`元素，进行`DOM`操作
   + 可在这发起后端请求，拿回数据，配合路由钩子做一些事情
5. `beforeUpdate()`

   + 数据更新时调用，发生在虚拟`DOM`重新渲染和打补丁之前；你可以在这个钩子中进一步地更改状态，这不会触发附加的重渲染过程
   + 此处获取的数据是更新后的数据，但是获取页面中的`DOM`元素是更新之前的
6. `updated()`

   + 组件`DOM`已经更新，所以你现在可以执行依赖于`DOM`的操作
   + 不要在此函数中操作数据，会陷入死循环
7. `activated()`

   + 在使用`vue-router`时有时需要使用`<keep-alive></keep-alive>`来缓存组件状态，这个时候`created`钩子就不会被重复调用了
   + 如果我们的子组件需要在每次加载的时候进行某些操作，可以使用`activated`钩子触发
8. `deactivated()`

   + `for keep-alive`组件被移除时使用
9. `beforeDestroy()`
   + 实例销毁之前调用；在这一步，实例仍然完全可用
+ 可做一些删除提示，如：你确认删除XX吗？
   + 可用于销毁定时器，解绑全局时间；销毁插件对象
10. `destroyed()`
    + 当前组件已被删除，销毁监听事件，组件，事件，子实例也被销毁
    + 这时组件已经没有了，你无法操作里面的任何东西了

### 子父组件的生命周期

+ 仅当子组件完成挂载后，父组件才会挂载
+ 销毁父组件时，先将子组件销毁后才会销毁父组件

## axios

> 功能强大的网络请求库
>
> 以`Promise`为基础的`HTTP`客户端，适用于：浏览器和`node.js`
>
> 封装`ajax`，用来发送请求，异步获取数据

+ 必须先导入才可使用
+ 使用`get`和`post`方法即可发送对应的请求
+ `then`方法中的回调函数会在请求成功或失败时触发
+ 通过回调函数的形参可以获取响应内容，或错误信息

## 组件

> 组件系统是`Vue`的另一个重要概念，因为它是一种抽象，允许我们使用小型、独立和通常可复用的组件构建大型应用
>
> 仔细想想，几乎任意类型的应用界面都可以抽象为一个组件树
>
> 创建组件的两种方式：全局组件；局部组件

### 使用组件

1. 创建组件构造器
2. 注册组件
3. 使用组件

``` html
<div id="example">
    <my-component></my-component>
</div>
		
<script src="vue.js"></script>
<script>
	// 1.创建组件构造器
	const myComponent = Vue.extend({
		template: "<h1>A custom component!</h1>"
	});
			
	// 2.注册组件，自定义标签名称
	Vue.component('my-component', myComponent);
			
	let app = new Vue({
		el: "#example"
	});
</script>
```

#### Vue.extend()

+ 调用`Vue.extend()`创建一个组件构造器
+ 通常在创建组件构造器时，传入`template`代表我们自定义组件的模板
+ 该模板就是在使用到组件的地方，要显示的HTML代码

#### Vue.component()

+ 调用`Vue.component()`将刚才的组件构造器注册为一个组件，并为其起一个标签名
+ 需要两个参数：注册组件的标签名，组件构造器
+ 组件必须挂载在某个组件下，否则不生效

### 全局组件

> 全局组件在所有的`vue`实例中都可以使用
>
> 先注册组件，再初始化根实例

``` html
<div id="app">
	<cpn></cpn>
</div>
<div id="app2">
	<cpn></cpn>
</div>

<script src="../vue.js"></script>
<script>
	// 1.创建组件构造器
	const cpnC = Vue.extend({
		template: "<h1>全局组件</h1>"
	});
			
	// 2.注册组件(全局组件)
	Vue.component('cpn', cpnC);
			
	const app = new Vue({
		el: "#app"
	});
    const app2 = new Vue({
		el: "#app2"
	});
</script>
```

### 局部组件

> 局部组件，是在某一个具体的`vue`实例中定义的，只能在这个`vue`实例中使用

``` html
<div id="app">
	<cpn></cpn>
</div>
		
<div id="app2">
	<cpn></cpn>
</div>
		
<script src="../vue.js"></script>
<script>
	// 1.创建组件构造器
	const cpnC = Vue.extend({
		template: "<h1>全局组件</h1>"
	});
			
	// 2.组测组件，局部组件
	const app = new Vue({
		el: "#app",
		components: {
			cpn: cpnC
		}
	});	
</script>
```

### 父组件和子组件

> 组件和组件之间存在层级关系，即：父子组件的关系

``` html
<div id="app">
	<cpn2>
	</cpn2>
</div>
		
<script src="../vue.js"></script>
<script>
	// 1.创建第一个组件构造器（子组件）
	const cpnC1 = Vue.extend({
		template: "<h2>子组件</h2>"
	});
			
	// 2.创建第二个组件构造器（父组件）
	const cpnC2 = Vue.extend({
		template: '<h1>父组件</h1> <cpn1></cpn1>',
		components: {
			cpn1: cpnC1
		}
	});
			
	// root组件
	const app = new Vue({
		el: "#app",
		components: {
			cpn2: cpnC2
		}
	});
</script>
```

### 注册组件的语法糖

``` html
<div id="app">
	<cpn1></cpn1>
	<cpn2></cpn2>
</div>
		
<script src="../vue.js"></script>
<script>
	// 注册全局组件
	Vue.component('cpn1', {
		template: "<h1>HelloWorld</h1>"
	});
			
	// root组件
	// 注册局部组件
	const app = new Vue({
		el: "#app",
		components: {
			'cpn2': {
				template: "<h2>我是局部组件</h2>"
			}
		}
	});
</script>
```

### 组件模板抽离

> 将`template`的`HTML`语法抽离出来，挂载到对应的组件是，使结构更清晰

``` html
<div id="app">
	<cpn></cpn>
	<cpn2></cpn2>
</div>
		
<!-- 1.使用script标签 模板抽离：类型必须为 text/x-template -->
<script type="text/x-template" id="cpn">
	<h1>script 模板抽离</h1>
</script>
		
<!-- 2.使用template标签 模板抽离 -->
<template id="cpn2">
	<h2>template 模板抽离</h2>
</template>
		
<script src="../vue.js"></script>
<script>
	Vue.component('cpn', {
		template: "#cpn2"
	});
			
	const app = new Vue({
		el: "#app",
	});
</script>
```

### 组件访问实例的数据

> 组件不能通过`{{}}`访问`Vue`实例中的`data`
>
> 组件对象有一个`data`属性，也可以有`methods`属性
>
> 此`data`属性必须是一个函数
>
> 函数内部返回一个对象，对象内部保存着数据

``` html
<div id="app">
	<cpn></cpn>
</div>
		
<template id="cpn">
	<div>
		<h1>{{ title }}</h1>
		<p>template 模板抽离</p>
	</div>
</template>
		
<script src="../vue.js"></script>
<script>
	Vue.component('cpn', {
		template: "#cpn",
		data() {
			return {
				title: "拿到数据了"
			}
		}
	});
			
	const app = new Vue({
		el: "#app",
	});
</script>
```

#### 为什么data必须是函数

+ 每次使用时都会产生一个新的对象，不同的`Vue`实例时，这个`data`是互相独立的

## 组件通信

### 父子组件间的通信

![image-20210321114712493](E:\我的坚果云\images\image-20210321114712493.png)

+ 父组件通过`props`向子组件传递数据
+ 子组件通过事件向父组件发送消息

#### 父传子

> 通过子组件`props`属性来传递数据`props`是一个数组
>
> 属性的值必须在组件中通过`props`属性显示指定；否则，不会生效
>
> 传递过来的`props`属性的用法与`data`属性的用法相同
>
> `props`避免使用驼峰命名：如`cStudent`应改为`c-students`

``` html
<div id="app">
	<cpn :cstudents="students"></cpn>
</div>
		
<template id="cpn">
	<div>
		<p>{{ cmessage }}</p>
		<ul>
			<li v-for="item in cstudents">{{ item }}</li>
		</ul>
	</div>
</template>
		
<script src="../vue.js"></script>
<script>
	// 子组件
	// 通过 props
	const cpn = {
		template: '#cpn',
		// 通过数组传值
		// props: ['cmessage', 'cstudents']
        
        // 需要进行类型验证时，需要此种写法
		props: {
			// 类型限制
			// cmessage: String,
			// cstudents: Array
					
			// 提供默认值，且是否必传
			cmessage: {
				type: String,
				default: "Hello",
				required: false
			},
					
			// 类型是数组或对象时，默认值必须为函数
			cstudents: {
				type: Array,
				default() {
					return ['Tom']
				}
			}
		}
	}
			
	// 父组件
	const app = new Vue({
		el: "#app",
		data: {
			message: "Hi!",
			students: ['Jack', 'Cai', 'Kate']
		},
		components: {
			cpn
		}
	});
</script>
```
#### 子传父

+ 在子组件通过`$emit()`来触发事件
+ 在父组件通过`v-on`来监听子组件的事件

``` html
<!-- 父组件模板 -->
<div id="app">
	<cpn @item-click="cpnClick"></cpn>
</div>
		
<!-- 子组件模板 -->
<template id="cpn">
	<div>
		<button v-for="item in categories" @click="btnClick(item)">{{ item.name }}</button>
	</div>
</template>
		
<script src="../vue.js"></script>
<script> 
	// 子组件
	const cpn = {
		template: "#cpn",
		data() {
			return {
				categories: [
					{id: "aaa", name: "热门推荐"},
					{id: "aaa", name: "手机数码"},
					{id: "aaa", name: "家用电器"},
					{id: "aaa", name: "电脑办公"}
				]
			}
		},
		methods: {
			btnClick(item) {
				// 发射事件到父组件：自定义事件
				this.$emit('item-click', item)
			}
		}
	}
			
	// 父组件
	const app = new Vue({
		el: "#app",
		components: {
			cpn
		},
		methods: {
			cpnClick(item) {
				console.log(item)
			}
		}
	});
</script>
```

## Vue-Cli

> `Vue`项目的脚手架：`vue`的项目结构，方便我们快速开发部署

### 安装

> 确保已经安装`node`和`npm`

+ 在命令行输入：`npm install --global vue-cli`：全局安装`vue-cli`

### 创建vue项目

+ 在命令行输入：`vue init webpack ____(项目名)`
+ 安装过程中出现`router`需要选择确定，之后会用到
+ `Use ESLint`：为代码审查
+ 为项目安装`npm(类似java中的maven)`：`npm install`
+ `npm run dev`：即可运行该项目

![image-20210321163201053](E:\我的坚果云\images\image-20210321163201053.png)

### 项目结构

![image-20210321163241264](E:\我的坚果云\images\image-20210321163241264.png)

+ `build`：配置了`webpack`的基本配置、开发环境配置、生产环境配置
+ `config`：配置了`webpack`路径端口值
+ `node_modules`：安装依赖代码块
+ `src`：存放源码和资源文件
  + `assets`： 静态资源，如：图片
  + `components`：组件文件夹，放`vue`的组件
  + `App.vue`：根组件，所有页面都是在`App.vue`下进行切换的，也可以理解为所有的路由也是`App.vue`的子组件
  + `main.js`：入口`js`文件，主要作用是初始化`vue`实例并使用需要的插件
+ `static`：存放第三方静态资源的
+ `.babelrc`：转换浏览器识别的JS语法（ES6、ES7)
+ `.editorconfig`：编辑器配置文件
+ `index.html`：文件入口
+ `package-lock.json & package.json` ：项目的包配置文件