# TypeScript





### 类型声明

可以在定义的变量后指定输出的变量类型，一旦定义后，变量的类型便不能更改。

- any:表示任何类型，可以赋值给任何类型的变量，关闭类型检测。
- unknown:表示未知类型的变量，实际上是一个类型安全的any，不能直接赋值给其他变量。

> *类型断言，可以用来告诉解析器变量的实际类型，e as string    |    < string>e*

- void:空值（undefined），一般用于函数的返回值。

- never:没有值，用于不会返回结果的函数.

- object:表示一个js对象，也可以通过{},来指定对象中必须包含的属性，eg {name:string};

> *{name : string , [propName : string ] : any};*表示一个对象里有name属性和有其他任意类型的属性。
>
> *函数接口的类型声明， 语法：(形参：类型，形参：类型...)=>返回值*



数组的表达方式：let e:  string[] ,或者 let g: Array[string];

元组（tuple）：固定长度的数组，eg,let h :[string, string ] ;

枚举：将所有可能的情况全部列出来，enum Gender{  Male ,  Female };

> *类型别名 通过 type mytype =  1| 2 | 3 | 4 | 5 ...,后续便可引用mytype* 



### 配置tsconfig.json文件

页面中添加了该文件，便可以使用tsc命令对所有ts文件进行编译，当然你也可以使用	tsc 【文件名】  -w对文件进行编译监听。

- include:用来指定那些ts文件需要被编译， 路径：**	表示任意目录，、 *表示任意文件
- exclude:不需要被编译的目录，默认值：【node_modules  ,  bower_components,  jspm_packages】
- extends:定义被继承的配置文件
- files:一个一个文件的指定需要编译，通常用于较少的文件项目
- compilerOptions:编译器的选项
	- target:用来指定ts被编译为es的版本("ES6"),默认转为ES3
	- module:指定要使用的模块化规范 
	- lib:用来指定项目中要使用的库，一般情况下不需要改
	- outdir:用来指定编译后的文件所在目录
	- outFile:将代码合并为一个文件
	- allowJs:是否对js文件进行编译，默认是false
	- checkJs:检查js代码是否符合规范，默认为false
	- removeComments:是否移除注释
	- noEmit:不生成编译后的文件
	- noEmitOnError:代码有错误不生成编译后的文件
	- alwaysStrict:用来设置编译后的文件是否使用严格模式
	- noImplicitAny:不允许隐式any
	- noImplicityThis:不允许不确定类型的this
	- strictNullChecks:严格检查空值
	- strict：所有严格检查的总开关，一旦写入所有都自动开启。



### webpack打包工具

1. 初始化项目
2. 下载依赖  cnpm i -D webpack webpack-cli  typescript  ts-loader
3. 编写webpack.config.js的配置文件
4. 编写ts.config.json文件
5. npm run webpack

```
const path=require("path")  //引入path包

moudle.exports={
	//指定入口文件
	entry:"./",
	//指定打包所在文件目录
	output:{
		path:path.resolve(__dirname,'dist'),//拼接目录防止出错
		//打包后文件名
		filename:"bundle.js"
	},
	
	//指定打包时要使用的模块
	moudle:{
	//指定加载的规则
	rules:[
	{
		//指定规则生效的文件
		test:/\.ts$/   ,//正则表达式，指定以ts结尾的文件
		//要使用的loader
		use:'ts-loader',
		//要排除的文件
		exclude:/node-modules/
	}
	]
	}
	
	
	
	


}
```

