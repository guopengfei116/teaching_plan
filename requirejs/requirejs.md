# requirejs
> requirejs是一个javaScript文件或者模块的加载器。
同时也是一个规范模块化开发的库。

## 相关概念与介绍

#### 模块
一个文件就是一个模块，这里的模块指js文件。

#### 模块加载器
相当于我们canvas课程中封装的图片加载器。
只不过一个加载img，一个加载js，文件类型不一样。

#### 规范模块化 
- 通常我们书写的模块整体都会采用一个自调函数包裹起来，即沙箱模式编写的模块。
- requirejs提供了独有的方式来规范模块的定义，这种方式定义的模块称为AMD模块。

#### 小结
requirejs主要提供了两大功能
    1. 加载模块 - 模块可以是AMD模块，也可以是普通模块
    2. 规范模块定义 - 有助于不同开发者模块的共享。

#### requirejs的好处
- 提高javaScript文件的加载速度，避免不必要的堵塞。
- 其独特的模块定义方式可显著减少全局变量污染。
- 其独特的模块定义方式可以在脚本层面申明模块的依赖。

## 实战演练

#### 3个全局变量
- requirejs一共对外暴露了3个全局变量
    1. requirejs - 用于加载模块
    2. require - 用于加载模块
    3. define - 用于定于模块
- 其中requirejs与require是同一个函数，关系类似与jQuery === $

#### require
- 作用：加载模块
- 语法：require([模块1, 模块2, 模块3, ...], function() {})
- 备注：第一个参数为加载的模块列表，
第二个参数可选，为模块加载完毕后的回调。

#### define
- 作用：定义模块
- 语法：define([模块1, 模块2, 模块3, ...], function() {})
- 备注：第一个参数为模块的依赖列表，
第二个参数为模块主体，通常是一个函数，实际上可以是任意数据类型。

#### require方法使用模块输出(即模块对外暴露的东西)

AMD模块
    - 如果模块主体是一个函数，那么函数的返回值即该模块的输出
    - 如果模块主体是其他数据类型，那么输出的就是数据本身

普通模块
    - 需要配置该模块中申明的全局变量，配置什么就输出什么
    - 如果不配置，什么都不输出，require会收到undefined值

## require.config
- 这是一个用于配置requirejs的方法，主要配置模块的加载地址与模块依赖
```javascript
require.config({

	// 配置所有模块的基础路径，这个基础路径自身相对于引入了requirejs的html文件路径
	baseUrl: 'js/', 
	
	// 给模块起名字，以后在define定义模块依赖或者require的时候，直接使用别名即可
	paths: {

		// key是模块的名字，value是模块的地址，该地址是基于baseUrl的
		模块名1: 模块地址1,
		模块名2: 模块地址2
	},
	
	// 配置普通模块的依赖与输出
	// 值为一个对象，其中key是模块的名字，value是可配置项
	shim: {
		
		模块名1: {

			// 配置该模块中申明的全局变量，最终变量的值会输出给require。
			exports: 'Bird'，

			// 配置该模块的依赖
			deps: ['模块1'， '模块2']
		},

		模块名2：{}
	}
});
```

#### 入口模块data-main
    在页面中引入requirejs的script标签，
可以通过添加data-main属性配置一个入口模块，
requirejs库自身加载完毕后，会在第一时间加载该模块。