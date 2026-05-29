## node.js和npm

node.js是浏览器引擎的JavaScript运行环境

npm是node.js默认的以JavaScript编写的软件包管理系统

###  查看版本

-v --vesion

### vue cli 和vite

vue cli是vue的命令行界面工具，是vue2用的，处于维护模式

npm instal -g @vue/cli

## 第一个vue程序

vue create hello-vue

cd hello-vue

npm run serve

## 使用 vite创建项目

### 安装 vite

npm install vite -g

vite -v

### 创建项目

npm create vue@3

![image-20260122150238830](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260122150238830.png)

![image-20260122150259144](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260122150259144.png)



![image-20260122150407854](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260122150407854.png)

![image-20260122150506992](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260122150506992.png)

## 使用cdn创建项目

![image-20260122151432495](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260122151432495.png)

新建文件cdn.html

输入html：5 用tab出现：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    
</body>
</html>
```

然后是

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="https://unpkg.com/vue@3"></script>
</head>
<body>
    <!-- 创建一个id位app的div元素，其将在vue应用中使用 -->
     <div id="app">{{message}}</div>
     <script>  
        // 从vue中解构出creatApp函数
        const {createApp}=Vue
        // 创建一个vue应用
        createApp({
            //data函数，用于定义应用中的数据
            data(){
                return {
                    message:'hello vue!',
                }
            },
        }).mount('#app')
     </script>
</body>
</html>
```

## mustache语法

```html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    //这里不要忘了引用下面这个CDN
    <script src="https://unpkg.com/vue@3"></script>
</head>
<body>
    <div id='app'>
        <sapne>我的名字：{{name}}</sapne>
    </div>
    <script>
        const{createApp}=Vue
        createApp({
            data(){
                return{
                    name:'huanhuan',
                }
            },
        }).mount('#app')
    </script>
</body>
</html>

```

## 常用指令：

#### v-if：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="https://unpkg.com/vue@3"></script>
</head>
<body>
    <div id='app'>
    	<div v-if="mycolor=='blue'">蓝</div>
    	<div v-else-if="mycolor=='green'">绿</div>
    	<div v-else-if="mycolor=='red'">红</div>
   		<div v-else>其他颜色</div>   
    </div>
    <script>
        const{createApp}=Vue
        createApp({
            data(){
                return{
                    mycolor:'red',
                }
            },
        }).mount('#app')
    </script>
</body>
</html>
```

#### v-show:

```html
<div v-show="mycolor=='red'">红</div>
<div v-show="mycolor=='blue'">蓝</div>   
```

#### v-for:

```html
<div v-for="fruit in fruits">{{fruit}}</div>
//这里index后面的括号要和in之间有空格，不然就报错了
<div v-for="(fruit,index) in fruits">{{index+1}}{{fruit}}</div>
```

#### v-text:

```html
<div>{{name}}</div>
<div v-text="name">我不会被渲染</div>
```

![image-20260124140323482](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260124140323482.png)

#### v-pre:

```
<div v-pre>{{name}}</div>
```

![image-20260124140440632](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260124140440632.png)

#### v-cloak:

如果一个页面的数据量很大并且使用了大量的数据绑定，那么可能会出现一个问题：用户会看到还没有编译完成的花括号标签，直到完全加载完成才可能显示实际渲染的内容，时可用

```html
<div v-cloak>{{name}}</div>
<style>
    [v-cloak]{
    display:none;
    }
</style>
```

#### v-html:

```html
<div v-html="html1"></div>
<div v-html="html2"</div>
```



#### v-once:

```html
<div>年龄: {{age}} </div>
<div v-once> 年龄: {{age}} </div>
<button @click="addAge">增加年龄</button>     
```

#### v-on:

绑定事件监听器

```html
<button v-on:click="reduceAge">减少年龄</button>
<button v-on:click.once="reduceAge">减少年龄</button>
<br/>
<input @keyup.enter="onEnter">
```

```
methods: {
                addAge(){
                    this.age++
                },
                reduceAge(){
                    this.age--
                },
                onEnter(event){
                    console.log("我输入的是：",event.target.value)
                }
            },
```

#### v-bind:

可动态绑定一个或多个class和style属性

```html
<div v-bind:class="{'red-div':mycolor=='blue'}">
    v-bind绑定class
</div>
<div :class="{'red-div':isRed}">
    v-bind绑定class简写
</div>
<img :src='imageurl' :style="{width:size+'px'}"/>
```

```
<style>
        [v-cloak]{
            display:none;
        }
        .red-div{
            color:red;
            background-color:yellow;
        }
```

```\
data(){
                return{
                    mycolor:'blue',
                    fruits:['苹果','香蕉','橘子'],
                    name:'huanhuan',
                    age:18,
                    html1:'<h1>hello vue</h1>',
                    html2:'<h2>{{name}}</h2>',
                    isRed:true,
                  imageurl:'https://acgknowimage.com/images/2026/01/22/26011103.png',
                    size:50,
                   
                }
            },
            
```

#### 完整代码：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="https://unpkg.com/vue@3"></script>
</head>
<body>
    <div id='app'>
    	<div v-if="mycolor=='blue'">蓝</div>
    	<div v-else-if="mycolor=='green'">绿</div>
    	<div v-else-if="mycolor=='red'">红</div>
   		<div v-else>其他颜色</div>

        <div v-show="mycolor=='red'">红</div>
        <div v-show="mycolor=='blue'">蓝</div>   
        
        <div v-for="fruit in fruits">{{fruit}}</div>
        <div v-for="(fruit,index) in fruits">{{index+1}}{{fruit}}</div>

        <div>{{name}}</div>
        <div v-text="name">我不会被渲染</div>

        <div v-pre>{{name}}</div>

        <div v-cloak>{{name}}</div>
        

        <div v-html="html1"></div>
        <div v-html="html2"></div>
        
        <div>年龄: {{age}} </div>
        <div v-once> 年龄: {{age}} </div>
        <button @click="addAge">增加年龄</button>
        <br>
        <hr>
        <button v-on:click="reduceAge">减少年龄</button>
        <button v-on:click.once="reduceAge">减少年龄</button>
        <br/>
        <input @keyup.enter="onEnter">

        <div v-bind:class="{'red-div':mycolor=='red'}">v-bind绑定class</div>
        <div :class="{'red-div':isRed}">v-bind绑定class简写</div>
        <img :src="imageurl" :style="{width:size+'px'}"/>

    </div>

    <style>
        [v-cloak]{
            display:none;
        }
        .red-div{
            color:red;
            background-color:yellow;
        }
    </style>
    <script>
        const{createApp}=Vue
        createApp({
            data(){
                return{
                    mycolor:'blue',
                    fruits:['苹果','香蕉','橘子'],
                    name:'huanhuan',
                    age:18,
                    html1:'<h1>hello vue</h1>',
                    html2:'<h2>{{name}}</h2>',
                    isRed:true,
                    imageurl:'https://acgknowimage.com/images/2026/01/22/26011103.png',
                    size:50,
                   
                }
            },
            methods: {
                addAge(){
                    this.age++
                },
                reduceAge(){
                    this.age--
                },
                onEnter(event){
                    console.log("我输入的是：",event.target.value)
                }
            },
        }).mount('#app')
    </script>
</body>
</html>
```

#### v-model:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="https://unpkg.com/vue@3"></script>
</head>
<body>
    <div id="app">
        <div>我的名字：{{name}}</div>
        <input
        :value="name"
        @input="event => name = event.target.value" />
        <br/>
        <input v-model="name" />
        <div>我的性别：{{sex}}</div>
        <select v-model="sex">
            <option disabled value="">请选择性别</option>
            <option>男</option>
            <option>女</option>
        </select>
    </div>
    <script>
        const { createApp } =Vue
        const app=createApp({
            data(){
                return{
                    name:'',
                    sex:''
                }
            },
        })
        app.mount('#app')
    </script>
</body>
</html>
```

#### v-model修饰符：

##### lazy修饰符：

会在每次input事件之后才更新数据

```
<input v-model.lazy="name" />
```

![image-20260124171819078](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260124171819078.png)![image-20260124171825847](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260124171825847.png)

##### number修饰符：

会自动将用户输入的内容转为数字类型

```
<div>我的年龄：{{age}}</div>
<input v-model="age"/>
<br/>
<input v-model.number="age"/>
```

![image-20260124172959849](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260124172959849.png)

##### trim修饰符：

自动去除输入内容两端的空格

```
<div>我的职业：{{profession}}</div>
<input v-model.trim="profession"/>
```

##### 完整代码：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="https://unpkg.com/vue@3"></script>
</head>
<body>
    <div id="app">
        <div>我的名字：{{name}}</div>
        <input
        :value="name"
        @input="event => name = event.target.value" />
        <br/>
        <input v-model.lazy="name" />

        <div>我的性别：{{sex}}</div>
        <select v-model="sex">
            <option disabled value="">请选择性别</option>
            <option>男</option>
            <option>女</option>
        </select>

        <div>我的年龄：{{age}}</div>
        <input v-model="age"/>
        <br/>
        <input v-model.number="age"/>

        <div>我的职业：{{profession}}</div>
        <input v-model.trim="profession"/>

    </div>
    <script>
        const { createApp } =Vue
        const app=createApp({
            data(){
                return{
                    name:'',
                    sex:'',
                    age:18,
                    profession:''
                }
            },
            watch:{
                age(value) {
                    console.log(typeof(value))
                }
            }
        })
        app.mount('#app')
    </script>
</body>
</html>
```

##  class属性绑定：

class是一种选择器，可以选择html中的元素及应用样式，可以选择任意数量的元素，可在多个元素中使用多次

### 绑定对象：

```
<body>
    <div id="app">
        <div :class="{'red-div':isRed}">class绑定对象</div>

    </div>
    <script>
        const{createApp}=Vue
        createApp({
            data(){
                return{
                    isRed:true
                }
            }
        }).mount("#app")
    </script>
    <style>
        .red-div{
            color:red
        }
    </style>
</body>
```

### 绑定计算属性：

```
<div :class="classobject">class绑定计算属性</div>
```

```
data(){
                return{
                    isRed:true,
                    isWhite:true,
                }
            },
            computed:{
                classobject(){
                    console.log('可以在这里写一段逻辑代码');
                    return{
                        'red-div':this.isRed,
                        'white-text':this.isWhite
                    }
                }
            },
```



### 绑定数组：

```
<div :class="[redclass,whiteclass]">class绑定数组1</div>

<div :class="[{'bold-text':isBold},redclass]">class绑定数组2</div>
```

### 完整代码：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="https://unpkg.com/vue@3"></script>
</head>
<body>
    <div id="app">
        <div :class="{'red-div':isRed}">class绑定对象</div>
        
        <div :class="classobject">class绑定计算属性</div>

        <div :class="[redclass,whiteclass]">class绑定数组1</div>

        <div :class="[{'bold-text':isBold},redclass]">class绑定数组2</div>
    </div>
    <script>
        const { createApp } =Vue
        createApp({
            data(){
                return{
                    isRed:true,
                    isWhite:true,
                    isBold:true,
                    redclass:'red-div',
                    whiteclass:'white-text',
                }
            },
            computed:{
                classobject(){
                    console.log('可以在这里写一些逻辑代码');
                    return{
                        'red-div':this.isRed,
                        'white-text':this.isWhite
                    }
                }
            },
            methods: {
                
            }
        }).mount('#app')
    </script>
    <style>
        .red-div{
            background-color:red
        }
        .white-text{
            color:white;
        }
        .bold-text{
            font-weight:bold;
        }
    </style>
</body>
</html>
```

## style属性绑定：

### 绑定对象：

```
<div :style="{'font-size':fontsize}"">style绑定对象1</div>
<div :style="styleobject">style绑定对象2</div>
```



### 绑定数组：

```
<div :style="[styleobject,backgroundcolor]">style绑定数组</div>
```



### 完整代码：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="https://unpkg.com/vue@3"></script>
</head>
<body>
    <div id="app">
        <div :style="{'font-size':fontsize}"">style绑定对象1</div>
        <div :style="styleobject">style绑定对象2</div>

        <div :style="[styleobject,backgroundcolor]">style绑定数组</div>
        
    </div>
    <script>
        const { createApp } =Vue
        const app=createApp({
            data(){
                return{
                    fontsize:'14px',
                    styleobject:{
                        'font-size':'17px',
                        color:'red'
                    },
                    backgroundcolor:{
                        'background-color':'blue'
                    },
                }
            },
            
        })
        app.mount('#app')
    </script>
</body>
</html>
```



### 自动前缀与样式多值：

当使用浏览器特有前缀的css属性时，vue会自动给他们加上相应的前缀。vue在运行时检查某个属性是否可以在当前浏览器中使用。如果浏览器不支持这个属性，那么将尝试各个浏览器支持的特殊前缀，找到哪个是被支持的。

-moz，火狐

-ms-（ie和edge）

```html
<div :style="{display:['-webkit-box','-ms-flexbox','flex']}"></div>
```

数组仅会渲染浏览器支持的最后一个值。在这个示例中，在支持不需要特别前缀的浏览器都会渲染为display：flex。

## css预处理器：

### Sass

#### 安装依赖：

```powershell
npm install sass sass-loader -D
或
yarn add sass sass-loader -D
```

#### webpack配置文件配置sass-loader

在vue.config.js文件中添加：

```js
module.exports={
  css:{
    loaderOptions:{
      sass:{
        additionalData: `@import "@/assets/styles/variables.scss";`
      }
    }
  }
}
```

在项目中创建style.scss文件，然后可以在其中编写sass代码，在.vue组件中，可以使用<style>标签来引入样式文件。

```html
<template>
    <div>
        <p class="text">
            {{message}}
        </p>
    </div>
</template>
<style lang='scss'>
    .text{
        color:$primary-color;
    }
</style>
```

Sass是一种css预处理器，而scss是sass3引入的新语法，是语法格式

#### 嵌套写法：

##### 基本选择器嵌套

css:

```css
.container{
	width:100%;
}
.container.title{
	font-size=24px;
}
.container.content{
    font-size:16px;
}
```

sass

```
.container{
	width:100%;
	.title{
		font-size=24px;
	}
	.content{
		font-size=16px;
	}
}
```

使用&选择器

css

```css
.button{
	background:blue;
}
.button:hover{
    background-color:red;
}
```

Sass

&表示.button本身

```
.button{
	background:blue;
	&:hover{
		background-color:red;
	}
}
```

#### 定义变量：

使用$符号，后面跟变量名和变量值

```
$primary-color:#007bff;

.button{
	background-color:$primary-color;
}
```

```
$font-size:16px;
$font-family:'Helvetica Neue',sans-serif;
$debug-mode:true;
$border-widths:1px 2px 3px 4px;
$colors:(primary:#007bff,secondary:#6c757d);
```

#### 模块系统：

是一种组织样式代码的方式，允许开发者将样式表分解成多个文件，并使用@import指令将这些文件组合在一起，形成一个完整的样式表

使用@import指令可以导入一个Sass模块

```
@import 'reset';
```

##### 混合指令：

使用@mixin关键字进行定义

```
@mixin button{
	display:inline-block;
	padding:0.5rem 1rem;
	font-size:1rem;
	line-height:1.5;
	color:#fff;
	background-color:#007bff;
	border-radius:0.25rem;
	text-align:center;
	text-decoration:none;
}
```

在样式表中，可以使用@include关键词引用该混合指令

```
.button{
	@include button;
}
```

```
@mixin button($bg-color){
	background-color:$bg-color;
}
.button-primary{
	@include button(#007bff);
}
.button-secondary{
	@include button(#6c757d);
}
```

#### 样式继承：

使用@extend指令实现，将一个选择器的样式规则继承到领域给选择器中

```
.button{
	display:inline-block;
	padding:0.5rem 1rem;
	font-size:1rem;
	line-height:1.5;
	color:#fff;
	background-color:#007bff;
	border-radius:0.25rem;
	text-align:center;
	text-decoration:none;
}
.button-primary{
	@extend .buttonn;
}
.button-secondary{
	@extend .button;
	background-color=#6757d;
}
```

![image-20260310185026162](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260310185026162.png)

#### 计算器实现

```
 <script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
    <style>
        .number-keyboard {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            padding: 10px;
            width: 320px;
            background-color: #dadada;
            border-radius: 8px;
        }
        .button-margin {
            margin: 5px;
            font-size: 20px;
            width: 60px;
            height: 60px;
            border-radius: 8px;
            background-color: #eee;
            border: none;
            outline: none;
            cursor: pointer;
            box-shadow: 2px 2px 4px rgba(0,0,0,0.3);
        }
        .button-selected {
            background-color: #3498db;
            color: white;
        }
        .display {
            width: 320px;
            height: 60px;
            font-size: 28px;
            background-color: #333;
            color: white;
            display: flex;
            justify-content: flex-end;
            align-items: center;
            padding: 0 15px;
            box-sizing: border-box;
            border-radius: 8px;
            margin-bottom: 10px;
            font-family: monospace;
        }
        body {
            display: flex;
            justify-content: center;
            padding-top: 50px;
            background: #f0f0f0;
        }
    </style>
</head>
<body>
    <div id="app">
        <div class="display">{{ displayText || '0' }}</div>
        <div class="number-keyboard">
            <button v-for="item in items" :key="item"
                @click="handleClick(item)" 
                class="button-margin"
                :class="{ 'button-selected': selectedButton === item }">
                {{ item }}
            </button>
        </div>
    </div>

    <script>
        const { createApp } = Vue

        createApp({
            data() {
                return {
                    items: ['7','8','9','/','4','5','6','*','1','2','3','-','C','0','=','+'],
                    displayText: '',
                    selectedButton: null
                }
            },
            methods: {
                handleClick(item) {
                    this.selectedButton = item

                    // 1. 清零
                    if (item === 'C') {
                        this.displayText = ''
                        return
                    }

                    // 2. 按等号计算
                    if (item === '=') {
                        if (!this.displayText) return
                        // 防止最后是运算符
                        let expr = this.displayText
                        if ('+-*/'.includes(expr.slice(-1))) {
                            expr = expr.slice(0, -1)
                        }
                        try {
                            this.displayText = eval(expr).toString()
                        } catch (e) {
                            this.displayText = '错误'
                        }
                        return
                    }

                    // 3. 连续运算符只保留最后一个
                    const lastChar = this.displayText.slice(-1)
                    if ('+-*/'.includes(lastChar) && '+-*/'.includes(item)) {
                        this.displayText = this.displayText.slice(0, -1) + item
                    } else {
                        this.displayText += item
                    }
                }
            }
        }).mount('#app')
```

## 数据响应式基础

### vue2中的数据响应式

机制简单易懂，但似乎在处理嵌套数据和数组时需要特殊处理，并且性能较低

会对每一个响应式数据对象执行递归遍历，并在每个属性上定义getter和setter函数来实现。当一个响应式数据的值发生改变时，框架就会检测到然后通知视图系统进行更新。

数据劫持

收集依赖

派发更新

### vue3中的数据响应式

使用proxy对象代理的方式，取代了Object.defineproperty 函数实现了更加高效且全面的响应式机制。

proxy是ES 6中新增的对象，可以拦截并改变js的底层操作

可用来包装一个对象，并拦截这个对象的属性访问、赋值、枚举等操作，从而实现自定义操作

在获取代理对象的属性时，proxy会拦截到get操作，收集该属性的依赖；会拦截到set操作，并在此时收集通知相关的依赖进行更新。

调用reactive函数将对象转化为响应式对象时，会递归地将对象的所有属性都转换为响应式对象。

响应原理更加高效和灵活，而且支持嵌套响应式对象和数组以及动态添加和删除属性等操作。

### proxy和Object.defineProperty的区别

功能：object.defineProperty主要用于检测对象属性的读取、赋值和删除等操作，而proxy可以拦截更多底层操作，包括has、set、deleteProperty、get、apply等，从而实现更细粒度的自定义操作和行为

监听：ob只能监听对象的属性变化，而proxy可以监听数个对象、对象的属性和数组等多种类型的对象变化情况

性能：proxy在底层实现时时直接拦截整个对象，而ob需要在每个属性上操作，监听越多，p性能优势越明显

兼容性：ob是ES 5标准

### 声明方法

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="https://unpkg.com/vue@3"></script>
</head>
<body>
    <div id="app">
        <button @click="handleClick">声明方法{{count}}</button>
    </div>
    <script>
        const{createApp}=Vue
        createApp({
            data(){
                return{
                    count:1
                }
            },
            methods:{
                handleClick(){
                this.count++;
                console.log('count='+this.count);
            }
        }
        }).mount('#app')
    </script>
</body>
</html>
```

不该在定义methods时使用箭头函数，因为箭头函数没有自己的上下文。

### DOM更新时机

当组件响应式数据变化时，Vue会立即执行DOM更新，把变化的部分渲染到虚拟DOM上，并标记需要更新的部分，过程同步执行

接着会在下一个微任务队列中执行一个flush阶段，把有需要更新的部分一次性批量更新到真实DOM上，这个过程是异步执行的。

Vue3采用新的编译器和渲染器

如果要等待DOM更新完成再相关的操作，则可以使用nextTick函数

```
import {nextTick} from 'vue'
nextTick(()=>{
//DOM更新后要执行的代码
})
```

nextTick是一个非常重要的API，用于在DOM更新之后执行一个回调函数

### 深层响应

新特性，使得Vue可以对嵌套的对象和数组进行更精细的响应式处理

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="https://unpkg.com/vue@3"></script>
</head>
<body>
    <div id="app">
        <button @click="handleClick">声明方法{{count}}</button>
        <br>
        <span>姓名:{{userInfo.name}} 年龄:{{userInfo.age}}</span>
        <button @click="changeUserInfo">深层响应</button>
    </div>
    <script>
        const{createApp}=Vue
        createApp({
            data(){
                return{
                    count:1,
                    userInfo:{
                        name:'张三',
                        age:18
                    }
                }
            },
            methods:{
                handleClick(){
                    this.count++;
                },
                changeUserInfo(){
                    this.userInfo.name='李四';
                    this.userInfo.age=20;
                }
            }
        }).mount('#app')
    </script>
</body>
</html>
```

点击按钮时直接修改内部的值，可以直接就能得到相应，Vue会自动响应更新，不需要手动调用$set方法

### 计算属性

computed，一种能够基于已有的响应式数据生成新的派升值computed Value的特殊属性

computed属性接受一个工厂函数（getter函数）作为参数，并返回一个响应式的Ref对象

```
<body>
    <div id="app">
        <div>姓名:{{userInfo.name}}</div>
        <div>是否成年:{{isAdult}}</div>
    </div>
    <script>
        const{createApp}=Vue
        createApp({
            data(){
                return{
                    userInfo:{
                        name:'张三',
                        age:18
                    }
                };
            },
            computed:{
                isAdult(){
                    return this.userInfo.age>=18?'成年':'未成年'
                }
            }
        }).mount('#app')
    </script>
</body>
</html>
```

 computed:{
                isAdult(){
                    return this.userInfo.age>=18?'成年':'未成年'
                }
            }

### computed和methods区别

```
<div>是否成年：{{isAdult()}}</div>

methods:{
	isAdult(){
		return this.userInfo.age>18 ?'已成年' :'未成年'
	}
}
```

```
 computed:{
                isAdult(){
                    return this.userInfo.age>=18?'成年':'未成年'
                }
            }
```

响应式依赖：computed会自动追踪依赖，只有相关响应式数据发生变化时才会重新计算；methods没有响应式依赖，每次使用都需要重新执行。

缓存机制：computed会缓存计算结果，只有在相关响应式数据发生变化时才会重新计算，提高了性能；methods没有缓存机制，每次使用都需要重新执行

使用场景：computed适合处理复杂的逻辑计算，并且计算结果需要被多次使用；methods适合处理简单的逻辑。

### computed的读写

#### getter函数

```
<div>{{fullname}}</div>

data(){
	reutrn{
		userInfo:{
			name:'zhangsan',
			age:17
		},
		firstnmae:'cai',
		lastname:'xukun'
	}
},
computed:{
	fullname(){
		return this.firstname+''+this.lastname;
	}
}
```

也可以把fullname改成以下代码

```
fullname：{
	get(){
		return ...
	}
}
```

#### setter函数

？？？？？？

```
<button @click="changefullname">修改fullname</button>

computed:{
	isAdult(){
		return this.userInfo.age>18?cheng:weicheng;
	},
}
fullname:{
	get(){
		return ..
	},
	set(newValue){
		const parts=newValue.split('');
		this.firstName=parts[0];
		this.lastName=parts[1];
	}
},

methods:{
	changefullname(){
		this.fullname='cai xukun';
	}
}
```

当修改fullname的值时，set函数就会通过newvalue接收新的值，此时只要把获得的值解析就可以

### 侦听器watch

用来响应数据变化并执行一些逻辑操作的，可监听一个或多个数据的变化情况，并在数据变化时自动执行回调函数。

```
<body>
    <div id="app">
        <p>问一个问题,我会回答是或否:
            <input v-model="question">
        </p>
        <p>回答:{{answer}}</p>
    </div>
    <script>
        const{createApp}=Vue
        createApp({
            data(){
                return{
                    question:'',
                    answer:'问题需要最后加?才能执行'
                }
            },
            watch:{
                question(newquestion){
                    if(newquestion.indexOf('?')>-1){
                        this.getAnswer();
                    }
                }
            },
            methods:{
                 async getAnswer() {
                    // 先判断是否包含?
                    if (!this.question.includes('?')) {
                        this.answer = '问题需要最后加?才能执行';
                        return;
                    }
                    this.answer = '思考中...';
                    try {
                        const res = await fetch('https://yesno.wtf/api');
                        const data = await res.json();
                        this.answer = data.answer === 'yes' ? '是' : '否';
                    } catch (error) {
                        this.answer = 'Error! 无法连接到 API: ' + error.message;
                    }
                }
            }
        }).mount('#app')
    </script>
```

![image-20260311102022180](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260311102022180.png)

![image-20260311101956565](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260311101956565.png)

![image-20260311101924008](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260311101924008.png)

### 深层侦听器

watch函数提供了deep选项来深度监听对象或数组的变化。当deep选项为true时，Vue会递归遍历对象或数组的所有属性。

应用场景包括以下：

对象或数组属性是响应式的，但新属性添加后需要进行响应式处理

无法预知对象或数组的层级结构，或者需要动态添加或删除属性

需要监听对象或数组中所有属性变化的情况。

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="https://unpkg.com/vue@3"></script>
</head>
<body>
    <div id="app">
        <h2>watch深度监听Demo</h2>
        <div>
            <label>
                first name:
            </label>
            <input v-model="userInfo.firstName">
        </div>
        <div>
            <label>
                last name:
            </label>
            <input v-model="userInfo.lastName">
        </div>
        <button @click="changeUserInfo">xiugaixinxi</button>
    </div>
    <script>
        const{createApp}=Vue
        createApp({
            data(){
                return{
                    userInfo:{
                        firstName:'',
                        lastName:''
                    }
                }
            },
            watch:{
                userInfo:{
                    handler(newVal,oldVal){
                        console.log(`旧的值为：${JSON.stringify(oldVal)}`);
                        console.log(`新的值为：${JSON.stringify(newVal)}`);
                    },
                    deep:true
                }
            },
            methods:{
                changeUserInfo(){
                    this.userInfo.firstName='cai';
                    this.userInfo.lastName='xukun';
                }
            }
        }).mount('#app')
    </script>
</body>
</html>
```

```
// 错误写法（单引号）：直接输出字符串 "${JSON.stringify(oldVal)}"
console.log('旧的值为：${JSON.stringify(oldVal)}'); 

// 正确写法（反引号）：解析模板字符串，输出实际的对象值
console.log(`旧的值为：${JSON.stringify(oldVal)}`); 
```



```
// 你的当前写法（有效）
this.userInfo.firstName = 'cai';
this.userInfo.lastName = 'xukun';

// 优化写法：一次性赋值，控制台会只打印一次变化
this.userInfo = {
  firstName: 'cai',
  lastName: 'xukun'
};
```

![image-20260311103712451](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260311103712451.png)

### 即时回调的监听器

watch默认是懒执行的，只有当被侦听的数据源发生变化时才会执行回调函数

为了实现即时回调，可以在watch选项对象中，通过设置immediate为true来实现

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="https://unpkg.com/vue@3"></script>
</head>
<body>
    <div id="app">
        <h2>watch即时回调Demo</h2>
        <div>
            <label>count:</label>
            <input v-model="count">
        </div>
        <div>
            <label>
                <label>Double count:</label>
                <span>{{doubleCount}}</span>
            </label>
        </div>
    </div>
    <script>
        const{createApp}=Vue
        createApp({
            data(){
                return{
                    count:1,
                    doubleCount:1
                }
            },
            watch:{
                count:{
                    immediate:true,
                    handler(newval,oldVal){
                        this.doubleCount=newval*2;
                    }
                }
            },
        }).mount('#app')
    </script>
</body>
</html>
```

![image-20260311104549305](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260311104549305.png)

### computed和watch的区别

#### 实现方式不同：

c是通过一个函数实现，这个函数包括所依赖的数据，当其中任何一个数据变化时，computed会重新计算结果并返回新值

watch是通过观察特定数据来实现的，一旦观察的数据发生变化，就会执行一个回调函数

#### 使用场景不同：

c返回计算结果，可以是任何值，包括原始类型，对象，数组

w没有返回值，他执行一个回调函数来响应数据变化

#### 支持异步：

c不支持

w支持

#### 是否有缓存：

c所依赖的属性不变时会调用缓存。

watch不支持缓存，每次监听的值发生变化都会调用回调。

### 购物车的实现：

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="https://unpkg.com/vue@3"></script>
</head>
<body>
    <div id="app">
        <h1>商品列表</h1>
        <ul>
            <li v-for="(product,index) in products" :key="index">
                {{product.name}}-{{product.price}}元
                <button @click="addToCart(index)">添加到购物车</button>
            </li>
        </ul>
        <h1>购物车</h1>
        <ul>
            <li v-for="(item,index) in cart" :key="index">
                {{item.name}}-{{item.price}}元-{{item.count}}件
                <button @click="removeProduct(index)">删除</button>
            </li>
        </ul>
        <div>
            <p>总金额:{{totalPrice}}元</p>
        </div>
    </div>
    <script>
        const{createApp}=Vue
        createApp({
            data(){
                return{
                    products:[
                        {name:'商品1',price:100},
                        {name:'商品2',price:200},
                        {name:'商品3',price:300}
                    ],
                    cart:[],
                }
            },
            methods:{
                addToCart(index){
                    const product=this.products[index];
                    const item=this.cart.find((item)=>item.name===product.name);
                    if(item){
                        item.count++;
                    }else{
                        this.cart.push({...product,count:1});
                    }
                },
                removeProduct(index){
                    var count=--this.cart[index].count;
                    if(count==0){
                        this.cart.splice(index,1);
                    }
                }
            },
            computed:{
                totalPrice(){
                    return this. cart.reduce((total,item)=>{
                        return total+item.price*item.count;
                    },0);
                },
            },
            watch:{
                cart:{
                    handler(newVal,oldVal){
                        console.log("购物车发生了变化",newVal);
                    },
                    deep:true,
                    immediate:true
                }
            }
        }).mount('#app')
    </script>
</body>
</html>
```



![image-20260311120007928](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260311120007928.png)

![image-20260311120053733](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260311120053733.png)

![image-20260311120135091](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260311120135091.png)

## 组件化开发

组件是由一个Vue实例定义的。可以通过Vue.createApp方法创建一个Vue应用程序实例，并通过组件选项对象来定义一个组件

组件时应用程序的核心之一， 是构建复杂应用程序的基本单位，可以帮助开发人员将应用程序拆分成多个可复用和可组合的部分，从而实现更高效、灵活可维护的开发

### vue中的组件

使用create组件构建项目时，vue会定义在一个单独的.vue文件中，称为单文件组件（SFC）

npm create vue@3

```
D:\vue3学习> npm create vue@3

> npx
> create-vue

┌  Vue.js - The Progressive JavaScript Framework
│
◇  请输入项目名称：
│  components
│
◇  请选择要包含的功能： (↑/↓ 切换，空格选择，a 全选，回车确认)
│  TypeScript
│
◇  选择要包含的试验特性： (↑/↓ 切换，空格选择，a 全选，回车确认)
│  none
│
◇  跳过所有示例代码，创建一个空白的 Vue 项目？
│  No

正在初始化项目 D:\vue3学习\components...
│
└  项目初始化完成，可执行以下命令：

   cd components
   npm install
   npm run dev

| 可选：使用以下命令在项目目录中初始化 Git：

   git init && git add -A && git commit -m "initial commit"

PS D:\vue3学习> cd components
PS D:\vue3学习\components> npm install

added 146 packages in 11s

29 packages are looking for funding
  run `npm fund` for details
```

```
PS D:\vue3学习\components> npm run dev

> components@0.0.0 dev
> vite


  VITE v7.3.1  ready in 4610 ms

  ➜  Local:   http://localhost:5173/
  ➜  Network: use --host to expose
  ➜  Vue DevTools: Open http://localhost:5173/__devtools__/ as a separate window        
  ➜  Vue DevTools: Press Alt(⌥)+Shift(⇧)+D in App to toggle the Vue DevTools
  ➜  press h + enter to show help

```

![image-20260311150221880](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260311150221880.png)

组件可以被多次使用，不需要重复编写代码

### 组件化思想

一种软件设计和开发思想，将系统软件划分为独立、可重用的组件，组件可在不同的应用程序中使用，被不同的开发者独立地开发、测试和维护

提高软件地可重用性、可维护性、可拓展性，降低组件之间地耦合性

### 定义一个组件

命名通常采用驼峰式，因为是合法的js标识符

MyComponent.vue

```
<script lang="ts">
//导出组件对象
    export default{
        data() {
            return{
                text:'',
                displayText:''
            }
        },
        methods:{
            showText(){
                this.displayText=this.text;
            }
        }
    }
</script>
<template>
    # 组件模板
    <div>
        <input v-model="text">
        <button @click="showText">显示</button>
        <div v-if="displayText">{{displayText}}</div>
    </div>
</template>
<style>
    button{
        margin-left: 10px;
    }
</style>
```

这个组件有script，template和style三个部分

分别需要用typescript、html和css代码来构建

使用SFC可以快速完成组件地构建和优化，包括自动提取CSS、代码差分、压缩和缓存等功能。

### 使用组件

打开App.vue

添加

```
import MyComponent from './components/MyComponent.vue'
```

```
    <MyComponent />
```

![image-20260311151807049](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260311151807049.png)

![image-20260311151821943](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260311151821943.png)

![image-20260311151931794](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260311151931794.png)

### 全局组件

每次都引入组件的路径有一些麻烦。

全局组件是在Vue应用程序中注册的组件，可以在任何地方使用

打开main.ts

```
import './assets/main.css'

import { createApp } from 'vue'
import App from './App.vue'

createApp(App).mount('#app')

```

修改如下：

```
import './assets/main.css'

import { createApp } from 'vue'
import App from './App.vue'
import MyComponent from './components/MyComponent.vue'

// 旧的写法
// createApp(App).mount('#app')


const app=createApp(App);
app.component('MyComponent',MyComponent);
app.mount('#app');
```



![image-20260311152811802](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260311152811802.png)

写法二具备更强的拓展性

写法一：链式调用，极简写法，把创建App、挂载DOM的操作一步完成

缺点：创建后无法再对它进行任何配置（比如注册全局组件、指令、过滤器、配置全局属性等）

写法二：先把createApp返回值赋给app，通过app变量进行任意配置，最后再挂载

接下来可以把import MyComponent删除并保存代码，如果仍可以正常显示组件，也就完成了注册。

```
在 main.ts 里，你已经通过 app.component('MyComponent', MyComponent) 把它注册成了全局组件，这意味着在整个应用的任何组件里，都可以直接使用 <MyComponent />，不需要再单独 import。
之前在 App.vue 里写的 import MyComponent 是局部引入的写法，现在既然已经全局注册了，这行 import 就可以删掉了。
保留 main.ts 里的 import MyComponent 是必须的，因为全局注册需要先把组件引入进来。
```

### 局部组件

就是在vue组件中注册的组件，仅可在该组件及子组件中使用。

全局组件：

通过app.component全局注册，可在应用程序的任何位置使用

不需要在每个组件中单独导入，方便全局使用

全局注册但未被使用的组件无法在生成打包时被自动移除，可能会导致打包文件过大

会使项目依赖关系变得不太明确，可能会影响应用程序长期的可维护性

局部组件：

通过components属性进行局部注册，只能在该组件及其子组件中使用

可在父组件中直接导入，使组件之间的依赖关系更加明确

对tree-shaking更加友好，不会包含未使用的组件，减少打包文件大小

在使用时需要在每个组件中单独导入，使用相对麻烦



插件unplugin-vue-components

既包含全局组件的优点，又包含局部组件的优点

在项目目录下使用命令行输入：

npm i unplugin-vue-components -D

![image-20260311163150000](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260311163150000.png)

加入

import Components from 'unplugin-vue-components/vite'

```
npm i unplugin-vue-components -D
# 或 yarn/pnpm
# yarn add unplugin-vue-components -D
# pnpm add unplugin-vue-components -D
```

### vue的生命周期

分为三个阶段

创建阶段、更新阶段、销毁阶段

#### setup函数

是vue3中新加入的一个生命周期函数，在组件实例被创建之前调用，并且只会被调用一次，其他生命周期函数都在他里面声明

该函数的返回值将作为组件的初始数据可以是一个对象或者一个函数，用于设置响应式数据、引用其他组件或者服务等。

在这个阶段，组件的生命周期钩子函数和响应式数据还没有设置

```
setup(props,context){
	console.log('setup')
	return {}
},
```

```
import {onoBeforeMount,onMounted,onBeforeUpdate,onUpdated,
onBeforeUmount,onUnmounted,onActivated,onDeactivated,onErrorCaptured from 'vue';}
```

#### onBeforMount函数

在组件挂载到页面之前调用onBeforeMount函数，此时组件的响应式数据已经被设置完整，但是组件的$el属性还没有被创建

```
setup(props,context){
	console.log('setup')
	onBeforeMount(()=>{
		console.log('onBeforeMount 组件将挂载到页面')
	})；
	return{}
},
```

#### onMounted函数

```
setup(props,context){
	console.log('setup')
	onMounted(()=>{
		console.log('onMounted组件已经挂载到页面')；
	});
	return{}
}
```

#### onUpdate函数

```
setup(props,context){
	console.log('setup')
	onUpdated(()=>{
		console.log('onUpdated组件已经更新');
	});
	return{}
}
```

#### onBeforeUnmount函数

```
setup(props,context){
	console.log('setup')
	
	onBeforeUnmount(()=>{
		console.log('。。。组件即将卸载');
	});
	return{}
},
```

#### onUnmounted函数

```
setup(props,text){
	console.log('setup')
	
	onBeforUnmount(()=>{
		console.log('...组件已经卸载');
	});
	return{}
};
```

#### onActivated函数

```
setup(props,context){
	console.log('setup')
	
	onActivated(()=>{
		console.log('...组件被激活');
	});
},
```

#### onDeactivated函数

```
setup(props,context){
	console.log('setup')
	
	onActivated(()=>{
		console.log('...组件被停用');
	});
},
```

#### onErrrorCaptured函数

```
setup(props,context){
	console.log('setup')
	...
	onErrorCaptured((error,vm,info)=>{
		console.log('onErrorCaptured')
		console.error('捕获到错误：',error);
		console.error('错误信息:',info);
	});
	return {}
},
```

setup可以进行一些初始化的操作并返回一个对象。这个对象的属性和方法可以在组件template中使用

### 父子组件的生命周期

新建ChildComponent.vue

```
<script lang="ts">
    import{ onBeforeMount, onMounted,onBeforeUpdate,onUpdated,onBeforeUnmount,onUnmounted,onActivated,onDeactivated,
        onErrorCaptured
    } from 'vue';

    export default{
        setup(){
            onBeforeMount(()=>{
                console.log('onBeforeMount');
            });
            onMounted(()=>{
                console.log('onMounted');
            });
            onBeforeUpdate(()=>{
                console.log('onBeforeUpdate');
            });
            onUpdated(()=>{
                console.log('onUpdated');
            });
            onBeforeUnmount(()=>{
                console.log('onBeforeUnmount');
            });
            onUnmounted(()=>{
                console.log('onUnmounted');
            });
            onActivated(()=>{
                console.log('onActivated');
            });
            onDeactivated(()=>{
                console.log('onDeactivated');
            });
            onErrorCaptured(()=>{
                console.log('onErrorCaptured');
            });
            return{}
        },
    }
</script>
<template>
    <div>
        我是子组件
    </div>
</template>
<style>
</style>
```

父组件MyComponent.vue如下：

```
<script lang="ts">
import ChildComponent from './ChildComponent.vue';

//导出组件对象
    export default{
        data() {
            return{
                text:'',
                displayText:''
            }
        },
        methods:{
            showText(){
                this.displayText=this.text;
            },
        },
        beforeCreate() { console.log('父 beforeCreate') },
        created() { console.log('父 created') },
        beforeMount() { console.log('父 beforeMount') },
        mounted() { console.log('父 mounted') },
        beforeUpdate() { console.log('父 beforeUpdate') },
        updated() { console.log('父 updated') }
    }
</script>
<template>
    # 组件模板
    <div>
        <input v-model="text">
        <button @click="showText">显示</button>
        <div v-if="displayText">{{displayText}}</div>
        <ChildComponent></ChildComponent>
    </div>
</template>
<style>
    button{
        margin-left: 10px;
    }
</style>
```

接下来在Myconponent.vue中引用这个子组件

```
<template>
    # 组件模板
    <div>
        <input v-model="text">
        <button @click="showText">显示</button>
        <div v-if="displayText">{{displayText}}</div>
        <ChildComponent></ChildComponent>
    </div>
</template>
```

![image-20260311171944381](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260311171944381.png)

父组件执行setup和onBeforeMount函数后，会先执行子组件的完整生命周期，然后才会执行父组件的onMounted

使用父组件给子组件传值时，需要使用v-if或watch监听，否则可能会导致子组件已经加载完毕，而值没有传递完成

### 组件的通信方式

#### 使用props和emit函数实现父子组件通信

这俩是最基本的组件通信方式

通过props函数父组件可以向子组件传递数据

通过emit函数，子组件可以向父组件发送事件

新建项目npm create vue@3

communication

ParentComponent.vue

```
<template>
    <div>
        <h2>父组件</h2>
        <p>当前消息：{{ message }}</p>
        <button @click="changeMessage">发送消息给子组件</button>
        <ChildComponent :message="message" @eventMessage="handleEventMessage"/>
    </div>
</template>
<script lang="ts">
    import ChildComponent from './ChildComponent.vue';
    import {ref} from 'vue';

    export default{
        components:{
            ChildComponent,
        },
        setup(){
            const message=ref('无');
            const changeMessage=()=>{
                message.value='父组件发出了新信息';
            };
            const handleEventMessage=(messageValue:string)=>{
                message.value=messageValue;
            }
            return{
                message,
                changeMessage,
                handleEventMessage,
            }
        }
    }
</script>
```

ChildComponent.vue

```
<template>
    <div>
        <h2>子组件</h2>
        <p>当前消息：{{ message }}</p>
        <button @click="sendMessage">向父组件发送消息</button>
    </div>
</template>
<script lang="ts">
    import {defineComponent} from 'vue';

    export default defineComponent({
        props:{
            message:{
                type:String,
                required:true,
            },
        },
        setup(props,{emit}){
            const sendMessage=()=>{
                const message='子组件发出了新信息';
                emit('eventMessage',message);
        };
        return{
            sendMessage,
        };
    },
    });
</script>
```



App.vue

```
<script setup lang="ts">
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
import ParentComponent from './components/ParentComponent.vue'
import ChildComponent from './components/ChildComponent.vue'
</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />
    </div>
  </header>

  <main>
    <ParentComponent />
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>

```

![image-20260311192617803](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260311192617803.png)

![image-20260311192627403](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260311192627403.png)

#### 使用Mitt实现组件之间的事件通信

Mitt是一个非常简单的事件总线库，支持很多高级特性，如异步事件、事件处理函数的移除和once方法等，可以让组件之间更灵活地通信，不必局限于父子关系或单向数据流

创建一个处理事件地文件event-bus.ts并输入以下代码

import mitt from 'mitt';

const bus=mitt();

export default bus;

之后用到Mitt的地方直接引入这个文件即可

新建SiblingComponent.vue，用于创建兄弟组件

这样的话其他文件也得改动

```
<template>
    <div>
        <h2>兄弟组件</h2>
        <p>当前消息：{{ state.message }}</p>
    </div>
</template>
<script lang="ts">
    import {defineComponent,reactive,onMounted} from 'vue';
    import bus from '@/event-bus';
    export default defineComponent({
        setup(props, ctx) {
            let state=reactive({
                message:'',
            });
            onMounted(()=>{
                bus.on('event',(msg):void=>{
                    console.log('兄弟组件收到消息:');
                    state.message=msg as string;
                });
            });
            return{
                state,
            };
        },
    });
</script>
```

![image-20260311201638638](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260311201638638.png)

![image-20260311201818168](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260311201818168.png)

### 使用Provide和Inject函数实现

父组件通过provide函数提供一个数据，子组件通过Inject函数注入该数据，在子组件中可以直接使用该数据

最大特点就是可以跨级传值，如从父组件到孙组件，不用一层层写props

新建GrandsonComponent.vue

```
<template>
    <div>
        <h2>孙子组件</h2>
        <p>Project/Inject传值：{{ provideValue }}</p>
    </div>
</template>
<script lang="ts">
    import {defineComponent,inject} from 'vue';
    export default defineComponent({
        setup(){
            const provideValue=inject<string>('provide');
            return{
                provideValue
            };
        },
    });
</script>
```

Inject函数的第一个参数是要获取的变量的键名，这个键名应该和祖先组件中Provide函数提供的键名一致，否则无法获取到正确的值。

![image-20260311203725866](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260311203725866.png)

![image-20260311203912805](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260311203912805.png)

### 制作代办列表页

新建TooItem.vue

```
<template>
    <div class="list" @dragover.prevent @drop="onDrop">
        <div class="list-header">
            {{ header }}
        </div>
        <ul>
            <li
            v-for="item in items"
            :key="item.id"
            class="list-item"
            draggable="true"
            @dragstart="onDragStart(item)"
            >{{ item.title }}
            </li>
        </ul>
    </div>
</template>
<script lang="ts">
    import { defineComponent } from 'vue';
    interface Item{
        id:number;
        title:string;
        status:'Todo' | 'Doing' | 'Done';
    }

    export default defineComponent({
        name:'TodoItem',
        props:{
            header:{
                type:String,
                required:true,
            },
            items:{
                type:Array,
                required:true,
            },
            onDragStart:{
                type:Function,
                required:true,
            },
            onDrop:{
                type:Function,
                required:true,
            },
        }
    })
</script>
<style scoped>
    .list{
        margin-left:16px;
        padding: 10px;
        border: 1px solid #ccc;
        border-radius: 5px;
        padding:10px;
        width:30%;
    }
    .list-header{
        font-size: 18px;
        font-weight: bold;
        margin-bottom:10px;
    }
    .list-item{
        background-color: #f5f5f5;
        border: 1px solid #ccc;
        border-radius: 5px;
        padding: 10px;
        margin-bottom: 5px;
        user-select:none;
    }
    .list-item:hover{
        background-color:#e0e0e0;
    }
</style>

```

TodoList.vue

```
<template>
    <div>
        <div class="container">
            <TodoItem header="Todo" :items="items.filter(item=>item.status==='todo')"
                :onDragStart="onDragStart" :onDrop="()=>onDrop('todo')">
            </TodoItem>

            <TodoItem header="Doing" :items="items.filter(item=>item.status==='doing')"
                :onDragStart="onDragStart" :onDrop="()=>onDrop('doing')">
            </TodoItem>
            
            <TodoItem header="Done" :items="items.filter(item=>item.status==='done')"
                :onDragStart="onDragStart" :onDrop="()=>onDrop('done')">
            </TodoItem>
        </div>
    </div>
</template>
<script lang="ts">
    import {ref,defineComponent} from 'vue';
    import TodoItem from './TodoItem.vue';

    interface Item{
        id:number;
        title:string;
        status:'todo' | 'doing' | 'done';
    }

    export default defineComponent({
        name:'TaskBoard',
        components:{
            TodoItem,
        },
        setup(){
            const items =ref<Item[]>([
                {id:1,title:'Task 1',status:'todo'},
                {id:2,title:'Task 2',status:'todo'},
                {id:3,title:'Task 3',status:'doing'},
                {id:4,title:'Task 4',status:'done'}
            ]);
            const onDragStart=(item:Item)=>{
                event?.dataTransfer?.setData('item',JSON.stringify(item));
            };
            const onDrop=(status:'todo' | 'doing' | 'done')=>{
                const item=JSON.parse(event?.dataTransfer?.getData('item') || '{}');
                item.status=status;
                const index=items.value.findIndex(element=>element.id===item.id);
                if(index!==-1){
                    items.value[index]=item;
                }
            };
            return{
                items,
                onDragStart,
                onDrop,
            };
        },
    })
</script>
<style>
    .container{
        display:flex;
        justify-content: flex-start;
        width:100%;
    }
</style>
```

App.vue

```
<script setup lang="ts">
import TodoList from './components/TodoList.vue'
</script>

<template>
  <TodoList />
</template>
<style scoped>
</style>

```

![image-20260312192425186](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260312192425186.png)

这些任务能互相拖动到其他里面

### 添加列表项组件的开发

新建AddTask.vue

```
<template>
    <div class="add-task">
        <input type="text" v-model="taskTitle" @keyup.enter="addTask" placeholder="输入代办事项" />
        <button @click="addTask">添加</button>
    </div>
</template>
<script lang="ts">
    import { defineComponent,ref } from 'vue';
    export default defineComponent({
        name:'AddTask',
        setup(_,{emit}){
            const taskTitle = ref('');

            function addTask(){
                if(taskTitle.value.trim()){
                    emit('addTask',taskTitle.value.trim());
                    taskTitle.value = '';
                }
            }
            return{
                taskTitle,
                addTask,
            };
        },
    });
</script>
<style>
    .add-task{
        display:flex;
        align-items:center;
        margin:16px;
        width:280px;
    }
    input{
        flex-grow:1;
        margin-right:16px;
    }
</style>
```

然后对TodoList.vue修改

```
<template>
    <div>
        <div class="container">
            <TodoItem header="Todo" :items="items.filter(item=>item.status==='todo')"
                :onDragStart="onDragStart" :onDrop="()=>onDrop('todo')">
            </TodoItem>

            <TodoItem header="Doing" :items="items.filter(item=>item.status==='doing')"
                :onDragStart="onDragStart" :onDrop="()=>onDrop('doing')">
            </TodoItem>
            
            <TodoItem header="Done" :items="items.filter(item=>item.status==='done')"
                :onDragStart="onDragStart" :onDrop="()=>onDrop('done')">
            </TodoItem>
        </div>
        <AddTask @addTask="addTask"></AddTask>
    </div>
</template>
<script lang="ts">
    import {ref,defineComponent} from 'vue';
    import TodoItem from './TodoItem.vue';
    import AddTask from './AddTask.vue';

    interface Item{
        id:number;
        title:string;
        status:'todo' | 'doing' | 'done';
    }

    export default defineComponent({
        name:'TaskBoard',
        components:{
            TodoItem,
            AddTask,
        },
        setup(){
            const items =ref<Item[]>([
                {id:1,title:'Task 1',status:'todo'},
                {id:2,title:'Task 2',status:'todo'},
                {id:3,title:'Task 3',status:'doing'},
                {id:4,title:'Task 4',status:'done'}
            ]);
            const onDragStart=(item:Item)=>{
                event?.dataTransfer?.setData('item',JSON.stringify(item));
            };
            const onDrop=(status:'todo' | 'doing' | 'done')=>{
                const item=JSON.parse(event?.dataTransfer?.getData('item') || '{}');
                item.status=status;
                const index=items.value.findIndex(element=>element.id===item.id);
                if(index!==-1){
                    items.value[index]=item;
                }
            };
            function addTask(title:string){
                items.value.push({
                    id:Date.now(),
                    title,
                    status:'todo',
                });
            }
            return{
                items,
                onDragStart,
                onDrop,
                addTask,
            };
        },
    })
</script>
<style>
    .container{
        display:flex;
        justify-content: flex-start;
        width:100%;
    }
</style>
```

![image-20260312193619258](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260312193619258.png)



![image-20260312193608110](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260312193608110.png)



## HTTP网络请求

http是一种无状态协议，这意味着每个请求和响应之间相互独立的，服务器不会记住之前的请求。

### Axios网络请求库

axios是一个基于promise的http客户端，可以在浏览器和Node.js环境中运行，使用XMLHttpRequest或Node.js的HTTP模板进行底层数据传输，并提供易于使用的API，方便开发者发送AJAX请求和处理相应

axios有以下优点

语法简单

支持浏览器和Axios：可以方便地在前端和后端实现一致的请求方式

支持取消请求：在处理大量请求时可能需要取消某些请求，可以有效减少服务器负载和网络传输

提供拦截器：可以在请求或响应被处理之前或之后进行拦截和修改

#### 发送第一条网络请求

![image-20260312202925876](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260312202925876.png)

这段代码使用composition API发送了一个HTTP GET请求。在组件的setup函数中使用onMounted钩子函数注册了一个回调函数，该函数会在组件挂载之后执行，并在控制台打印响应数据。

#### 使用测试接口调试网络请求

一些免费测试接口

JSONPlaceholder

ReqRes

Mockaroo

Postman Echo

### http基础知识

http是前后端数据传输的核心

新的网络通信协议，如websocket和http/2等

#### 常见的请求类型与用途

GET

 POST

 PUT：传输替换目标资源。资源更新、文件上传等

 DELETE

 HEAD

 OPTIONS获取支持的方法。跨域访问、api文档生成

 CONNECT要求在与代理服务器通信时建立隧道。加密代理、websocket通信等

 TRACE追踪请求-响应。调试、诊断、性能分析

GET和POST区别：

后退按钮刷新： 无害  | 数据会被重新提交

书签/缓存/历史： 有 | 无

编码类型： application/x-www-form-urlencoded | ~或multipart/form-data。为二进制数据使用多重编码

数据长度限制：受浏览器限制 | 无限制

数据类型限制： 只允许ASCII字符 | 无限制

可见性： 数据在url中对所有人可见、请求保存在历史记录中 | 数据保存在主题中，请求不会保存在历史记录中

#### put请求方法

一种用于封信资源的请求方法，与post请求方法在于，put请求方法时幂等的，即调用一次或连续多次时等价的，没有副作用，而连续调用多次post方法可能会有副作用

#### delete请求方法

状态码202 表示请求的操作可能会成功执行，但尚未开始执行

204 表示操作已经执行，无进一步的相关信息

200 ok，表示一致性，响应中提供了相关状态的描述信息

#### head请求方法

与get请求区别在于，仅返回报文首部，不返回主题

#### options

用于获取目的资源所支持的通信选项

#### connect

主要用于代理服务器转发客户端的请求到服务器端，通常在ssl/tls加密通信通信的代理服务器中

#### trace

主要用于对连接进行诊断，它会在响应报文中返回客户端发出的请求报文的首部字段，从而可以在接收方查看请求报文是否被修改

#### patch

对已知资源进行局部更新的请求方法，它与put请求方法有些类似，但是put请求方法要求客户端提供一个完整的资源表示，而patch请求方法只需要提供更细资源的内容

### 解读http状态码的含义

1xx，信息状态码，接收的请求正在处理

2xx，成功~，处理完毕

3xx，重定向状态码，需要进行附加操作完成请求

4xx，客户端错误状态码，服务器无法处理请求

5xx，服务端错误状态码，服务器处理请求出错



```
<script setup lang="ts">
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
import axios from 'axios';
import {onMounted} from 'vue';

onMounted(()=>{
  axios.get('https://jsonplaceholder.typicode.com/todos/1',{
    headers:{
    'Content-Type':'application/json',
    'Authorization':'Bearer'+'your token'
    }
  }).then(response=>{
    console.log(response);
  }).catch(error=>{
    console.log(error);
  })
})

</script>
```

#### 一次完整的网络请求过程

解析url

dns解析

建立tcp连接

发送http请求

服务器处理请求

服务器返回http响应

服务器接受http响应

渲染页面

关闭tcp连接

### https简介

与http明文传输相比，https即将内容加密，https的最后一个字母S指SSL（安全套接层）/TLS（安全传输协议），介于HTTP和TCP/IP之间。

使用了非对称加密方式。私钥只存在于服务器上，服务器发送的内容不可能被伪造，因为别惹你没有私钥，所以无法加密。

所有人都有公钥，但私钥只有服务器有，因此服务器才能看到被加密的内容。

### https的工作原理

发送方将信息的哈希值一起发送过去，接收方会把解密后的数据与哈希值进行对比，避免被篡改。

https由权威机构颁布CA（电子商务认证授权机构）证书，使用证书校验机制放置第三方伪装。

哈希值通过哈希算法压缩后得到的数据值

### 申请https证书

ios提交至app store的应用必须使用https进行网络请求才能通过审核

申请方式很简单，找到卖https证书的网站，然后找到CA证书服务，填写信息后购买即可

### https未全面普及的原因

建立连接需要额外时间和计算资源

增加服务器负担，吞吐量降低

https证书并非免费

兼容性问题

追求更快速度和更高吞吐量的网站或应用来说，可以选择使用http

### 跨域问题及其解决方案

在vue三开发中，经常会遇到需要向其他域名下的API发送请求的情况，这就是跨域请求

跨域请求是跨源资源共享CORS的简称，通常指客户端通过浏览器向服务器发起请求，但请求的url的协议、域名、端口号与当前页面的url不同

跨域请求会遇到浏览器的同源策略限制。同源策略指js只能访问与当前页面同源的资源，不能直接访问不同源的资源。同源指协议、域名和端口号相同。

cors机制分为简单请求和非简单请求。

简单请求，浏览器会自动在请求头加上Origin字段，表示请求来自哪个源，并向服务端发送一个预检请求，服务器根据信息决定是否允许跨域。

对于非简单，会在实际发送请求前发送一次options请求进行预检，服务端根据预检请求终端信息决定是否跨域。

### 使用JSONP实现跨域数据请求

原理是利用script标签的src属性不受同源策略限制的特性，在客户端动态创建一个script标签，将需要请求的数据作为参数传递给服务器，服务器将函数调用中返回给客户端，接收后执行

```
 npm install jsonp --save
```

```
import json form 'jsonp';
const url='http://example.com/api';
const params={
	id:'123';
	callback:'handleResponse'
}
jsonp(url,params,(err,data)=>{
	if(err){
		console.error(err);
	}else{
		console.log(data);
	}
});
```



### 	借助反向代理解决跨域问题

原理是在同一个域名下，利用服务器端来dialing客户端的请求，将客户端的请求转发到需要访问的目标服务器上，从而克服了跨域请求的限制。

在实现反向代理的时候，可以使用常见的web服务器，如nginx和apache等，通过相关配置实现反向代理功能。

反向代理可以实现更加安全可靠的跨域请求，同时可以在服务器端进行一些处理，如负载均衡、缓存等。



```
npm install http-proxy-middleware --save-dev
```

```
const {createProxyMiddleware} =require('http-proxy-middleware');
module.exports={
	devSever:{
		proxy:{
			'/api':{
				target:'https://api.example.com',
				changeOrigin:true,
				pathRewrite:{
					'^/api':'',
				},
			},
		},
	},
};
```

使用createProxyMiddle函数创建了一个代理服务器，并设置请求路径以/api

开头的请求都会被代理到目标服务器https://api.example.com上。其中，changeOrigin设置为true表示在请求头添加Origin字段，pathPewrite用于重写请求路径。

在Axios中发送请求时，将请求的路径改为代理服务器的地址，代码如下

```
axios.get('/api/data').then(response=>{
	console.log(response.data);
})
```

这样成功使用反向代理解决了跨域请求的问题。

### 封装Axios

在src下创建一个文件夹request，在目录下创建axiosInstance.ts



```
import axios from 'axios';
import {AxiosInstance,AxiosRequestConfig,AxiosResponse} from 'axios';
class AxiosInstanceClass{
    private readonly instance:AxiosInstance;
    constructor(config?:AxiosRequestConfig){
        this.instance=axios.create(config);
        this.instance.interceptors.request.use(
            (config)=>{
                return config;
            },
            (error)=>{
                return Promise.reject(error);
            }
        );
        this.instance.interceptors.response.use(
            (response)=>{
                return response;
            },
            (error)=>{
                return Promise.reject(error);
            };
        );
    }
    public async get<T any,R=AxiosResponse<T>>(url:string,config?:AxiosRequestConfig):Promise<R>{
        return this.instance.get<T,R>(url,config);
    }
    public async post<T any,R=AxiosResponse<T>>(url:string,data?:T,config?:AxiosRequestConfig):Promise<R>{
        return this.instance.post<T,R>(url,data,config);
    }
    public async put<T any,R=AxiosResponse<T>>(url:string,data?:T,config?:AxiosRequestConfig):Promise<R>{
        return this.instance.put<T,R>(url,data,config);
    }
    public async delete<T any,R=AxiosResponse<T>>(url:string,config?:AxiosRequestConfig):Promise<R>{
        return this.instance.delete<T,R>(url,config);
    }
    public async request<T any,R=AxiosResponse<T>>(config:AxiosRequestConfig):Promise<R>{
        return this.instance.request<T,R>(config);
    }
    const axiosInstance=new AxiosInstanceClass({
        baseURL:'https://jsonplaceholder.typicode.com',
        timeout:10000,
    });
    export default axiosInstance;
}

```

通过baseURL配置项设置了请求的基础URL，这样在请求时就可以省略域名部分，先填写为jsonplaceholder的域名

最后App.vue并输入以下代码进行网络请求测试

```
import axiosInstance from '@/request/axiosInstance';

	axiosInstance.get('todos/1')
	.then((response)=>{
		console.log('axiosInstance');
		console.log('response');
	})
	.catch(error=>{
		console.error(error);
	})
```

使用Vue Router构建单页应用

在传统的多页应用中，每个页面都是独立的，由服务器渲染返回给服务器，每个用户单词点击链接都需要重新向服务器请求新页面并重新加载整个页面。

在单页应用中，只是通过路由的切换来呈现不同的内容，减少了页面切换时的网络请求，提高用于体验。

Vue Router 时Vue官方开发的路由管理器。允许开发者在单页应用程序（SPA）中实现基于组件的导航。可以方便地在应用程序中进行路由配置，包括定义路由和路由参数，并实现页面之间的跳转和传递参数等功能。

还提供了一些高级功能，如路由守卫、动态路由和命名路由

守卫路由可以用于在路由跳转前进行一些拦截操作

动态路由可以根据不同的参数动态生成路由

命名路由可以方便进行路由跳转和参数传递



创建项目，并在创建过程中勾选Router

```
npm install vue-router
yarn add vue-router
```

#### 使用RouterLink创建导航链接

打开App.vue

```
<RouterLink to="/">Home</RouterLink>
<RouterLink to="/about">About</RouterLink>
```

指向两个路径，当用户单机这些链接时，Vue Router会根据响应的路由配置加载相应的组件

<router-link :to"{name:'about',params:{msg:123}}">About</router-link>

打开sr/router/index.ts

```
import {createRouter,createWebHistory} from 'vue-router'

import HomeView from '../views/HomeView.vue'
const router=createRouter({
	histroty:createWebHistory(import.meta.env.BASE_URL),
	routers:[
		{
			path:'/',
			name:'home',
			component:HomeView
		},
		{
			path:'/about',
			name:'about',
			component:()=>import('../views/AboutView.vue')
		}
	]
})

//导出路由实例
export default router
```



history参数表示路由模式，使用了createWebHistory方法，表示使用HTML5 history模式进行路由导航。该方法需要传入一个基础URL，可以通过import.meta.env.BASE_URL

routes参数表示路由配置

“/“路径指向了HomeView组件，可以通过name属性设置路由名称为’home‘

'/about'路径指向了一个懒加载的组件，可以通过name属性设置路由名称为'about'

'/about'路径对应的组件中使用了import，意味着当路由被访问时，该组件会被异步加载。这样可以提高应用程序的性能和加载速度，特别是当应用程序较大时明显。

打开mian.ts

```
import {createApp} from 'vue'
import App from './App.vue'
import router from './router'
import './assets/main.css'

const app=createApp(App)
app.use(router)
app.mount('#app')
```

#### 使用RouterView渲染路由页面

用于显示路由组件的组件

路由配置中的每个路由都映射到一个组件中，当访问路由时，该组件会被加载显示在RouterView组件中。因此，该组件可以让应用程序根据路由动态显示不同组件

```
<template>
	<header>
		<img alt="vue logo" class="logo" src="@/assets/log.svg" width="125" height="125">
		<div class="wrapper">
		<HelloWorld msg="you did it！">
		<nav>
			<RouterLink to="/">Home</RouterLink>
			<RouterLink to="/about">About</RouterLink>
		</nav>
		</div>
    </header>
    <RouterView>
</template>
```

随着单机不同的RouterLink，右侧RouterView绑定的显示内容就会实时更新

#### 动态路由

指在路由配置中可以包含动态参数，这些参数可以根据不同的请求动态地改变路由的匹配机制

动态路由可以用创建可复用的路由组件，并且根据参数的不同动态地加载数据和渲染页面

修改index.ts

```
routers:{
	path:'/',
	name:'home',
	component:HomeView
},
{
	path:'/about/:id',
	name:'about',
	component:()=>import('../view/AboutView.vue')
}
```

修改App.vue和AboutView.vue

```
<RouterLink to="/about/你好啊">About</RouterLink>
```

```
<h1>This is an about page{{$route.params.id}}</h1>
```

#### 嵌套路由

指在一个路由中嵌套另一个路由，也就是将一个路由组件作为另一个路由组件地子组件，只需将嵌套的路由配置添加到父路由的children数组中即可

可以根据需要在某个路由中显示不同的内容，而不必将所有内容都放在同一个组件中

在src/views目录下新建两个子页面Dashboard.vue和Profile.vue

```
<template>
    <div class="Profile">
        <h1>Profile</h1>
    </div>
</template>
```

```
<template>
    <div class="Dashboard">
        <h1>Dashboard</h1>
    </div>
</template>

```

然后再index.ts注册

```
 routes: [
    {
      path: '/',
      name: 'home',
      component: HomeView,
      children:[
        {
          name:'dashboard',
          path:'/',
          component:()=>import('../views/Dashboard.vue')
        },
        {
          name:'profile',
          path:'/profile',
          component:()=>import('../views/Profile.vue')
        }
      ]
    },
```

最后还需要修改HomeView.vue，因为还缺少RouterView

```
 <!-- 关键：子路由渲染的容器！必须加这个 -->
    <router-view />
```



```
<script setup lang="ts">
</script>

<template>
  <main>
    <RouterLink to="/dashboard">Dashboard</RouterLink>
    <RouterLink to="/profile">Profile</RouterLink>
    <RouterView/>
  </main>
</template>
<style scoped>
  a{
    margin-right:16px;
  }
</style>

```

```
import { createRouter, createWebHistory } from 'vue-router'
// 导入你的组件
import Home from '@/views/Home.vue' // 主页面
import Dashboard from '@/views/Dashboard.vue' // Dashboard页面
import Profile from '@/views/Profile.vue' // Profile页面（如果有的话）

const router = createRouter({
  history: createWebHistory(import.meta.env.BASE_URL),
  routes: [
    {
      path: '/',
      name: 'home',
      component: Home, // 主页面作为父路由
      children: [
        // 子路由：路径不要加 /，会基于父路径拼接
        { path: 'dashboard', name: 'dashboard', component: Dashboard },
        { path: 'profile', name: 'profile', component: Profile }
      ]
    }
  ]
})

export default router
```

#### 路由懒加载

优化应用程序性能

指在需要时才加载特定的路由组件，而不是一次性加载所有的路由组件，减少初始化时间

是使用ES 6 的动态import方法实现的。可以使用import方法异步加载一个模块，然后使用Webpack代码分割功能将这个模块打包成一个独立的块chunk，在路由访问时才会加载

如果要使用，需要在路由配置中将懒加载的路由组件的component属性设置为要给函数，会返回一个import方法。

例如about组件：

{

path:'/about/:id',

name:'about',

component:()=>import('../views/AboutView.vue')

}

当路由被访问时，about组件会被异步加载并渲染。由于组件时在运行阶段进行的，所以不能在编译时进行类型检查

### 路由的跳转

可以供通过编程式导航和声明式导航两种方式实现。

声明式指在模板中使用RouterLink来实现

编程式如下：

在组件中使用$router对象即可完成路由的挑战

```
<script setup lang="ts">
</script>

<template>
  <main>
    <RouterLink to="/dashboard">Dashboard</RouterLink>
    <RouterLink to="/profile">Profile</RouterLink>
    <button @click="toProfile">编程式导航</button>
    <RouterView/>
  </main>
</template>
<script lang="ts">
import type {Router} from 'vue-router'
import { useRouter,RouterLink,RouterView } from 'vue-router'
export default{
  setup(){
    const router:Router=useRouter()
    const toProfile=():void=>{
      router.push('/profile')
    }
    return{
      toProfile
    };
  },
};
</script>
<style scoped>
  a{
    margin-right:16px;
  }
</style>

```

### 路由的传参

路由跳转时，需要将一些数据传递给目标页面，这时需要使用路由传参。

传参同样是分为编程式导航和声明式导航

声明式传参在RouterLink中填写参数即可

编程式传参可以使用params和query参数进行传参

新建ParamsView.vue和QueryView.vue

```
<template>
    <div class="Query">
        <h1>Query{{ $route.query.msg }}</h1>
    </div>
</template>
<script lang="ts">
    import { useRoute } from 'vue-router'
    export default{
        name:'Query',
        setup() {
            const route=useRoute()
            console.log(route.query)
        },
    }
</script> 

```

```
<template>
    <div class="Params">
        <h1>Params{{ $route.params.id }}</h1>
    </div>
</template>
<script lang="ts">
    import { useRoute } from 'vue-router'
    export default{
        name:'Params',
        setup() {
            const route=useRoute()
            console.log(route.params)
        },
    }
</script>
```

在index.ts注册组件



```
<script setup lang="ts">
</script>

<template>
  <main>
    <RouterLink to="/dashboard">Dashboard</RouterLink>
    <RouterLink to="/profile">Profile</RouterLink>
    <button @click="toProfile">编程式导航</button>
    <button @click="toParams">编程式导航到Params</button>
    <button @click="toQuery">编程式导航到Query</button>
    <RouterView/>
  </main>
</template>
<script lang="ts">
import type {Router} from 'vue-router'
import { useRouter,RouterLink,RouterView } from 'vue-router'
export default{
  setup(){
    const router:Router=useRouter()
    const toProfile=():void=>{
      router.push('/profile')
    }
    const toParams=():void=>{
      router.push({name:'params',params:{id:123}})
    }
    const toQuery=():void=>{
      router.push({name:'query',query:{msg:123}})
    }
    return{
      toProfile
      ,toParams
      ,toQuery
    };
  },
};
</script>
<style scoped>
  a{
    margin-right:16px;
  }
  button{
    margin-right:16px;
  }
</style>

```

![image-20260313213111436](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260313213111436.png)

![image-20260313213121857](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260313213121857.png)



### 路由守卫：导航前的权限检查

验证用户是否已经登录或者是否具有访问权限等。

全局前置守卫和路由独享的前置守卫

全局守卫可以使用router.beforeEach方法注册，接受一个回调函数作为参数，该回调函数会在每次路由切换前执行

修改index.ts

```
import { createRouter, createWebHistory } from 'vue-router'
import HomeView from '../views/HomeView.vue'
import Dashboard from '../views/Dashboard.vue'
import Profile from '../views/Profile.vue'

const router = createRouter({
  history: createWebHistory(import.meta.env.BASE_URL),
  routes: [
    {
      path: '/',
      name: 'home',
      component: HomeView,
      children:[
        {
          name:'dashboard',
          path:'/',
          component:()=>import('../views/Dashboard.vue')
        },
        {
          name:'profile',
          path:'/profile',
          component:()=>import('../views/Profile.vue')
        },
        {
          name:'query',
          path:'/Query',
          component:()=>import('../views/QueryView.vue')
        },
        {
          name:'params',
          path:'/Params/:id',
          component:()=>import('../views/ParamsView.vue')
        }
      ]
    },
    {
      path: '/about/:id',
      name: 'about',
      // route level code-splitting
      // this generates a separate chunk (About.[hash].js) for this route
      // which is lazy-loaded when the route is visited.
      component: () => import('../views/AboutView.vue'),
      component: () => import('../views/AboutView.vue'),
    }
  ],
})
router.beforeEach((to, from, next) => {
  // to and from are both route objects. must call `next`.
  console.log(to)//即将要进入的目标路由对象
  console.log(from)//当前导航正要离开的路由对象
  next();//必须被调用才能进入下一个钩子函数，否则路由不会切换
})

export default router

```

![image-20260316155649062](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260316155649062.png)

### 解析守卫：导航中的数据解析

该方法会在路由解析组件之前执行

router.beforeRsolve((to,from,next)=>{

​	console.log('开始解析了')

 	next();

})

![image-20260316160023943](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260316160023943.png)

后置守卫：导航后的逻辑处理

在导航成功完成后被调用，与前置不同，后置守卫无法阻止导航完成，因为所有的钩子函数已经被调用了。主要用于执行一些与导航有关的异步操作或者动画效果

```
router.afterEach((to,from)=>{
  console.log('后置守卫生效')
  console.log(`Navigation to ${to.fullPath} from ${from.fullPath}`)
})
```

![image-20260316161637012](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260316161637012.png)

点击导航按钮会出现

![image-20260316161650512](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260316161650512.png)

如果不想全局监听，只想监听单独的某一个路由跳转

```
children:[
        {
          name:'dashboard',
          path:'/',
          component:()=>import('../views/Dashboard.vue'),
          beforeEnter:(to,from,next)=>{
            console.log('进入了dashboard路由')
            next()
          }
        },
```

![image-20260316162103901](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260316162103901.png)

### 路由权限控制

这次使用ui框架

```
npm install element-plus --save
```

UserList.vue

```
<template>
    <div>
        <el-table :data="userList" border>
            <el-table-column prop="name" label="姓名" />
            <el-table-column prop="age" label="年龄" />
            <el-table-column prop="email" label="邮箱" />
        </el-table>
    </div>
</template>

<script setup lang="ts">
    import {reactive} from 'vue'
    interface User{
        name:string,
        age:number,
        email:string
    }
    const userlist : User[]=reactive([
        {name:'张三',age:18,email:'zhangsan@example.com'},
        {name:'李四',age:20,email:'lisi@example.com'},
        {name:'王五',age:22,email:'wangwu@example.com'},
        {name:'赵六',age:24,email:'zhaoliu@example.com'},
        {name:'钱七',age:26,email:'qianqi@example.com'},
        {name:'孙八',age:28,email:'sunba@example.com'},
        {name:'周九',age:30,email:'zhoujiu@example.com'},
        {name:'吴十',age:32,email:'wushen@example.com'},
    ])
</script>
```

Userinfo.vue

```
<template>
    <el-card :body-style="{display:'flex','align-items':'center','font-size':'20px'}">
    <div class="avatar">
        <img src="@/assets/avatar.jpg" alt="用户头像">
    </div>
    <div class="user-details">
        <h3>{{ user.name }}</h3>
        <p>年龄：{{ user.age }}</p>
        <p>邮箱：{{ user.email }}</p>
        <p>分数：{{ user.score}}</p>
    </div>
    </el-card>
</template>
<script setup lang="ts">
    import {ref} from 'vue'
    interface User{
        name:string,
        age:number,
        email:string,
        score:number
    }
    //使用ref创建响应式的对象
    const user=ref<User>({
        name:'张三',
        age:18,
        email:'zhangsan@example.com',
        score:90
    })
</script>
<style scoped>
    .user-info-card{
        height:100%;
    }
    .avater img{
        width:120px;
        height:120px;
        border-radius:50%;
        object-fit:cover;
    }
    .user-details{
        margin-left:20px;
    }
</style>
```

上一个时用户列表，这个页面则是用户详细页。之后会再创建一个登录页，并通过权限控制未登录的用户禁止查看用户详情页。

目前还没有把创建的页面添加到路由中，因为后面还需要对权限进行一些处理。

![image-20260316211739861](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260316211739861.png)



新建Login.vue

```
<template>
    <div>
        <el-form v-if="!loggedIn" ref="ruleFormRef" :model="ruleForm" status-icon:rules="rules" label-width="120px">
            <el-form-item label="用户名" prop="username">
                <el-input v-model="ruleForm.username" autocomplete="off"></el-input>
            </el-form-item>
            <el-form-item label="密码" prop="password">
                <el-input v-model="ruleForm.password" type="password" autocomplete="off"></el-input>
            </el-form-item>
            <el-form-item>
                <el-button type="primary" @click="submitForm(ruleFormRef)">提交</el-button>
                <el-button @click="resetForm(ruleFormRef)">重置</el-button>
            </el-form-item>
        </el-form>
        <div v-else>
            <el-button type="primary" @click="logout">退出登录</el-button>
        </div>
    </div>
</template>

<script lang="ts" setup>
    import {reactive,ref,onMounted} from 'vue'
    import type {FormInstance,FormRules} from 'element-plus'

    const ruleFormRef=ref<FormInstance>()
    const loggedIn=ref<boolean>(false)

    const checkUsername=(rule:any,value:any,callback:any)=>{
        if(!value){
            return callback(new Error('请输入用户名'))
        }
        callback()
    }

    const validatePass=(rule:any,value:any,callback:any)=>{
        if(value===''){
            callback(new Error('请输入密码'))
        }else{
            callback()
        }
    }

    cosnt ruleForm=reactive({
        username:'',
        password:''
    })

    const rules=reactive<FormRules>({
        username:[
            {validator:checkUsername,trigger:'blur'}
        ],
        password:[
            {validator:validatePass,trigger:'blur'}
        ]
    })

    const submitForm=(formEl:FormInstance| undefined)=>{
        if(!formEl){
            return
        }
        formEl.validate((valid)=>{
            if(valid){
                localStorage.setItem('username',ruleForm.username)
                loggedIn.value=true
                formEl.resetFields()
            }else{
                return false
            }
        })
    }

    const resetForm =(formEl:FormInstance | undefined)=>{
        if(!formEl){
            return
        }
        formEl.resetFields()
    }

    const logout=()=>{
        localStorage.removeItem('username')
        loggedIn.value=false
    }

    onMounted(()=>{
        const username=localStorage.getItem('username')
        if(username){
            loggedIn.value=true
        }
    })
</script>
```

模板部分：使用条件渲染根据用户是否登录来显示不同内容。如果未登录，显示登录表单，如果已登录，则显示提示信息和退出按钮



数据部分：使用reactive函数创建了一个响应式的ruleForm对象，该对象包含用户名和密码的属性。使用ref创建了一个响应式的loggdIn变量，用于跟踪用户的登录状态。

校验规则：定义了校验用户名和密码的验证器函数checkUsername和validatePass，并将其添加到rules对象中，以便在表单验证时进行校验

方法：submitForm方法用于提交表单，将用户名保存到localStorage中并将loggedIn设置为true，表示用户已登录。resetForm方法用于重置表单。logout方法用于消除localStorage中的用户名并将loggedIn设置为false，表示用户已退出

生命周期钩子函数：使用onMounted钩子函数，在组件挂载后检查localStorage中是否存在用户名，如果存在，则将loggedIn设置为true，表示用户已登录

#### 路由权限

修改index.ts

```
import { createRouter, createWebHistory } from 'vue-router'
import HomeView from '../views/HomeView.vue'
import { ro } from 'element-plus/es/locale/index.mjs'

const router = createRouter({
  history: createWebHistory(import.meta.env.BASE_URL),
  routes: [
    {
      path: '/',
      name: 'home',
      component: HomeView,
    },
    {
      path: '/about',
      name: 'about',
      // route level code-splitting
      // this generates a separate chunk (About.[hash].js) for this route
      // which is lazy-loaded when the route is visited.
      component: () => import('../views/AboutView.vue'),
    },
    {
      path:'/login',
      name:'login',
      component:()=>import('../views/Login.vue')
    },
    {
      path:'/userlist',
      name:'userlist',
      component:()=>import('../views/UserList.vue')
    },
    {
      path:'/userinfo',
      name:'userinfo',
      component:()=>import('../views/UserInfo.vue')
    },
  ],
})

router.beforeEach((to,from,next)=>{
    const username=localStorage.getItem('username')
    if(!username && to.fullPath =='/userinfo'){
        next('/login')
    }else{
        next();
    }
})

router.beforeResolve((to,from,next)=>{
    console.log('开始解析了')
    next();
})

router.afterEach((to,from)=>{
    console.log('后置守卫生效')
    console.log(`Navigated to ${to.fullPath} from ${from.fullPath}`)
})

export default router

```

修改App.vue

```
<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
import UserInfo from './views/UserInfo.vue'
</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />
      <UserInfo />
      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
        <RouterLink to="/userinfo">UserInfo</RouterLink>
        <RouterLink to="/login">Login</RouterLink>
        <RouterLink to="/userlist">UserList</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>

```

![image-20260316231746211](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260316231746211.png)

## vuex的基本用法

vuex是一个用于状态管理的官方库。它提供了一个中央存储库来帮助管理和共享应用程序的状态。vuex允许开发人员将应用程序的状态（用户信息、主题设置、购物车数据）集中到单一状态树中，并以可预测的方式进行修改。

vuex使用了基于proxy的响应式系统，使得状态变化可以得到更好的追踪和优化，同时提高了性能。还支持在组件中使用composition api，使得编写可重用性和组合性的代码更容易。

npm install vuex --save

index.ts

``` 
import {createStore,Store} from 'vuex'
interface State {
  count:number
}
const state: State = {
  count:0
}

const getters={
  doubleCount(state:State){
    return state.count*2
  }
}

const mutations ={
  increment(state:State){
    state.count++
  }
}

const actions={
  incrementAsync({commit}:{commit:Function}){
    setTimeout(()=>{
      commit('increment')
    },1000)
  }
}

//创建vuex存储实例
const store:Store<State>=createStore<State>({
  state,
  getters,
  mutations,
  actions
})

export default store
```

main.ts

```
import './assets/main.css'
import store from './store'

import { createApp } from 'vue'
import App from './App.vue'
import router from './router'

const app = createApp(App)

app.use(router)
app.use(store)

app.mount('#app')

```

HomeView.vue

```
<script lang="ts">
import TheWelcome from '../components/TheWelcome.vue'
import { defineComponent,computed } from 'vue'
import { useStore } from 'vuex'

export default defineComponent({
  setup(){

    //使用useStore获取vuex store存储实例
    const store=useStore()

    //使用computed创建计算属性来获取状态和getters
    const count=computed(()=>store.state.count)
    const doubleCount =computed(()=>store.getters.doubleCount)

    const increment=()=>{
      store.commit('increment')
    }

    //定义异步增加计数的方法
    const incrementAsync=()=>{
      store.dispatch('incrementAsync')
    }

    // ✅ 关键：返回模板需要的变量和方法
    return {
      count,
      doubleCount,
      increment,
      incrementAsync
    }

  }
})
</script>

<template>
  <div>
    <p>当前计数：{{count}}</p>
    <p>当前计数的两倍：{{doubleCount}}</p>
    <button @click="increment">同步增加</button>
    <button @click="incrementAsync">异步增加</button>
  </div>
</template>

```

![image-20260317170854749](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260317170854749.png)

点同步会同时变化，点异步会停留一秒后变化

等价形式

```
const increment=()=>{
      store.commit('increment')
    }
```

最基础的等价写法（普通函数）

```
// 函数表达式（和你的写法功能完全一致）
const increment = function() {
  store.commit('increment');
};

// 函数声明（适合需要提升作用域的场景）
function increment() {
  store.commit('increment');
}
```

解构 commit 的简化写法（推荐）

```
import { useStore } from 'vuex';

const store = useStore();
// 解构出 commit 方法
const { commit } = store;

// 等价写法（直接调用解构后的 commit）
const increment = () => {
  commit('increment');
};

// 甚至可以进一步简化为一行（无额外逻辑时）
const increment = () => commit('increment');
```

在 Vue 选项式 API 中的等价写法

如果你的组件用的是选项式 API（而非 `<script setup>`），等价写法如下：

```
<script lang="ts">
export default {
  methods: {
    // 选项式 API 中，this 指向组件实例，可直接访问 $store
    increment() {
      this.$store.commit('increment');
    }
  }
};
</script>
```

## vuex的核心概念

### state：共享状态数据

用于储存整个应用的状态数据

```
interface state{
	count:number
}
```

```
const state:State={
	count:0
}
```

在组件中访问State

this.$store.state.count

### Getter:计算派生状态

根据state中的状态计算出新的值

```
const getters={
	doubleCount: (state:State)=>{
		return state.count*2
	}
}
```

this.$store.getters.doubleCount



Mutation:同步修改状态

修改state中状态的方法

```
const mutations={
	increment(state:State){
		state.count++;
	}
}
```

this.$store.commit('increment')



### Action:分发与处理异步任务

不会直接修改状态，而是提交Mutation

```
1秒后处理
const actions={
	incrementAsync({commit}:{commit:Function}){
		setTimeout(()=>{
			commit('increment')
		})
	}
}
```

this.$store.dispatch('incrementAsync')

### Moudule:模块化组织状态

每个模块可以拥有自己的状态，getter，mutation，action

```
const moduleA={

​	state:{...},

​	mutations:{...},

​	actions:{...},

​	getters:{...}

}

const store=new Vuex.Store({

​	modules:{

​		a:moduleA

​	}

})


```

## vuex的使用技巧

在web应用程序中，用户在与应用程序交互时，应用程序状态的改变通常是不可避免的，状态持久化可将数据或存储状态存储在本地存储或其他持久化存储中，从而保证数据或状态的持久性。

vuex持久化配置

方式一：手动利用html5的本地存储

111

方式二：使用vuex-persistedstate插件

安装vuex-persistedstate

```
npm install vuex-persistedstate --save
```

在store/index.ts

```
import {createStore,Store} from 'vuex'
import createPersistedState from 'vuex-persistedstate'
interface State {
  count:number
}
const state: State = {
  count:0
}

const getters={
  doubleCount(state:State){
    return state.count*2
  }
}

const mutations ={
  increment(state:State){
    state.count++
  }
}

const actions={
  incrementAsync({commit}:{commit:Function}){
    setTimeout(()=>{
      commit('increment')
    },1000)
  }
}

//创建vuex存储实例
const store:Store<State>=createStore<State>({
  state,
  getters,
  mutations,
  actions,
  plugins: [createPersistedState()],
})

export default store
```



![image-20260317182037436](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260317182037436.png)

插件自动把数据保存在了Vuex的key中

默认情况下，数据会存储在localstorage中，如果要将数据存储再sessionStorage中，需要以下配置

```
//创建vuex存储实例
const store:Store<State>=createStore<State>({
  state,
  getters,
  mutations,
  actions,
  plugins: [createPersistedState({
    storage: window.sessionStorage,
  })],
})
```

## 使用浏览器插件调试vuex

Vue.js devtools

111



## 使用nvm管理npm的版本

优点

管理多个Node.js版本

灵活性和可靠性

安装和升级Node.js

兼容性和跨平台



在github上找链接下载后

nvm --version

### nvm的常用指令

安装某个版本的node.js

nvminstall 14.16.0 

查看已安装的所有node.js版本

```
nvmlist
```

选择使用某个版本

nvmuse 18.15.0

## 使用Vuex处理登录信息

npm install vuex --save

store/index.ts

```
import {createStore}from 'vuex'
interface State {
  isLoggedIn:boolean,
}
const state: State = {
  isLoggedIn:false,
}
export default createStore({
  state,
  mutations: {
    setLoggedIn(state:State,isLoggedIn:boolean){
        state.isLoggedIn=isLoggedIn;
    },
  },
  actions:{},
  modules:{},
})
```

安装持久化插件

npm install vuex-persistedstate --save

修改index.ts

```
vuex-persistedstate 导入错误
提示：模块"vuex-persistedstate"没有导出的成员"createPersistedState"
新版 vuex-persistedstate 的导出方式变了，不能直接用 import { createPersistedState }，要改成 import createPersistedState。
```



```
import { createStore, Store } from 'vuex'
import createPersistedState from 'vuex-persistedstate'

// 1. 定义 State 接口（约束状态类型）
interface State {
  isLoggedIn: boolean
}

// 2. 初始化状态
const state: State = {
  isLoggedIn: false
}

// 3. 整合所有配置，创建唯一的 store
const store: Store<State> = createStore({
  // 状态
  state,
  // 同步修改状态的方法
  mutations: {
    setLoggedIn(state: State, isLoggedIn: boolean) {
      state.isLoggedIn = isLoggedIn
    }
  },
  // 异步操作（这里暂时为空，可根据需求添加）
  actions: {},
  // 模块（这里暂时为空，可根据需求添加）
  modules: {},
  // 插件：开启持久化（默认存储在 localStorage）
  plugins: [createPersistedState()]
})

// 4. 导出唯一的 store 实例
export default store
```

安装element plus

npm install element-plus --save

修改main.ts

```
import './assets/main.css'
import store from './store'
import ElementPlus from 'element-plus'
import 'element-plus/dist/index.css'
import { createApp } from 'vue'
import App from './App.vue'
import router from './router'

const app = createApp(App)
app.use(store)
app.use(ElementPlus)
app.use(router)

app.mount('#app')

```

App.vue

这里教材没有给出

```
<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
import LoginModal from './components/LoginModal.vue';
import {useStore} from 'vuex'
import {ref} from 'vue'
const dialogVisible = ref(false)
</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />
      <el-button type="primary" @click="dialogVisible = true" style="margin: 10px 0;">
        点击登录
      </el-button>
      <LoginModal v-model:visible="dialogVisible" />
      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>

```



### 制作登陆弹窗

components下新建LoginModal.vue

```
<template>
    <el-dialog title="登录" v-model="dialogVisible" :before-close="reset">
        <el-form ref="formRef" :model="submitInfo" :rules="rules" label-width="80px">
            <el-form-item label="用户名" prop="username">
                <el-input v-model="submitInfo.username" placeholder="请输入用户名"></el-input>
            </el-form-item>
            <el-form-item label="密码" prop="password">
                <el-input v-model="submitInfo.password" placeholder="请输入密码" type="password"></el-input>
            </el-form-item>
            <el-form-item>
                <el-button type="primary" @click="login(formRef)">登录</el-button>
                <el-button @click="reset">取消</el-button>
            </el-form-item>
        </el-form>
    </el-dialog>
</template>

<script lang="ts">
    import {defineComponent, ref,reactive} from 'vue'
    import {useStore} from 'vuex'
    import type {FormInstance,FormRules} from 'element-plus'
    import {watch} from 'vue'
    
    export default defineComponent({
        props:{
            visible:{
                type:Boolean,
                default:false
            },
        },
        setup(props,{emit}){
            const dialogVisible=ref(props.visible)
            const formRef=ref<FormInstance>()
            const rules=reactive<FormRules>({
                username:[{required:true,message:'请输入用户名',trigger:'blur'}],
                password:[{required:true,message:'请输入密码',trigger:'blur'}],
            })
            const store=useStore()
            const submitInfo=reactive({
                username:'',
                password:'',
            })
            watch(
                ()=>props.visible,
                (newValue)=>{
                    dialogVisible.value=newValue
                }
            )
            const reset=()=>{
                submitInfo.username=''
                submitInfo.password=''
                dialogVisible.value=false
                emit('update:visible',false)
            }
            const login=async(formEl:FormInstance|undefined)=>{
                if(!formEl)return
                await formEl.validate((valid,fields)=>{
                    if(valid){
                        dialogVisible.value=false
                        emit('update:visible',false)
                        store.commit('setLoggedIn',true)
                        localStorage.setItem('username',submitInfo.username)
                        localStorage.setItem('password',submitInfo.password)
                    }else{
                        console.log('登录失败')
                    }
                })
            }
            return{
                dialogVisible,
                rules,
                formRef,
                submitInfo,
                reset,
                login,
            }
        },
    })
</script>
```

通过v-model绑定dialogVisible变量控制对话框的显示和隐藏

const dialogVisible = ref(false)

  <LoginModal v-model:visible="dialogVisible" />

对话框内部使用el-from创建一个表单，并使用ref指令创建了一个表单引用formRef

在setup函数中，使用reactive函数创建了一个响应式对象rules，其中包含对账号和密码输入框的验证规则

watch函数用于监听props.visible的变化，一旦props.visible的值发生变化，就将值赋给dialogVisible，从而同步控制对话框的显示和隐藏方法

reset方法用于重置表单和对话框的状态，通过emit函数触发一个名为update：visible事件，并将false作为参数传递出去

login方法是一个异步函数，用于执行登陆操作，首先会检查formEl是否存在，如果不存在则返回。然后使用formEl.validate方法对表单进行验证，传入一个诡吊函数，当验证完成时会调用该回调函数。

App.vue

```
<script lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
import LoginModal from './components/LoginModal.vue'
import {defineComponent, ref,computed} from 'vue'
import {useStore} from 'vuex'

export default defineComponent({
  components:{
    LoginModal,
    HelloWorld,
  },
  setup() {
    const store=useStore()
    const loginModalVisible=ref(false)
    const login=computed(()=>store.state.isLoggedIn)
    
    const showLoginModal=()=>{
      loginModalVisible.value=true
    
    }
    const logout=()=>{
      store.commit('setLoggedIn',false)
      localStorage.removeItem('username')
      localStorage.removeItem('password')
    }
    return{
      loginModalVisible,
      login,
      showLoginModal,
      logout,
    }
  },
})
</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld :msg="'登录状态:'+login"/>
      <el-button type="primary" @click="showLoginModal">点击登录</el-button>
      <el-button @click="logout">点击退出登录</el-button>

      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>
    </div>
  </header>
  
  <LoginModal v-model:visible="loginModalVisible" />

  <RouterView />
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>

```

![image-20260323190256078](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260323190256078.png)



```
msg=""：传递字符串字面量（固定文本）
:msg=""：传递JavaScript 表达式 / 变量（动态值）
（: 是 v-bind: 的简写，核心作用是「把引号里的内容当 JS 代码解析」）
```

helloworld组件接受一个动态的msg属性，通过计算属性login将登陆状态和静态文本拼接起来作为msg传递给helloworld组件

使用ref函数创建了一个名为loginModalVidsible的响应式引用变量，用于控制登录和模态框的显示和隐藏

使用computed函数创建了一个计算属性login，该属性用于store中的isLoggedIn状态

定义了一个showLoginModal方法，调用该方法时，将loginModalVisible的值设为true，从而显示登录模态框

定义了一个logout方法，当调用该方法时，通过store.commit方法将isLoggedIn状态设置为中溢出保存的用户名和密码

## 项目构建利器-webpack

是一个静态模块打包器，它的主要目标时通过许多分散的模块（包括JS、html、css和图像等）打包成一个或多个优化的捆绑包，提高开发效率和程序性能

### 入口：构建起点与模块依赖

将使用./src/index.js作为入口点，可以在webpack配置文件中自定义这个设置

module.exports={

​	entry:'./path/t0/entry/file.js',

};

### 输出：构建结果的路径与命名

告诉webpack打包后的代码应该放在哪个文件中以及如何命名这个文件

默认情况下，输出在./dist/main.js

可以在webpack配置中自定义这个配置

```
const path=require('path');
module.exports={
	ouput:{
		path:path.resolve(__dirname,'dist'),
		filename:'my-first-webpack.budle.js',
	},
};
```

### loader加载器：处理各类资源转换

能够让webpack理解并处理javascript和json以外的其他类型的文件。可使用加载器来处理.txt文件：

```
module.exports={
	module:{
		rules:[{test:/\.txt$/,use:'raw-loader'}],
	},
};
```

### 插件：优化构建流程与结果

使用插件时只需要使用require函数便可以将其添加到plugins数组中

```
const HtmlWebpackPlugin=require('html-webpack-plugin');
module.exports={
	plugins:[new HtmlWebpackPlugin({template:'./src/index.html'})],
};
```

上面的例子中，使用html-webpack-plugin生成了一个html文件，并将自动生成的所有bundle注入此文件

### 模式：指定构建环境与优化celue

webpack的mode参数development、production或none允许指定当前的构建环境，默认值是production

```
module.exports={
	mode:'production',
};
```

### 浏览器的兼容性与环境运行要求

支持所有符合ES 5标准的浏览器

## webpack的使用技巧

### 代码拆分

如果将所有代码打包成一个文件，那么用户在首次访问网站时可能需要加载一个非常大的文件，从而导致加载时间过长

#### 入口起点entry point

使用entry配置时最简单直观的方式

现有如下目录结构

webpack-demo

|-package.json

|-webpack.config.js

|-/src

​	|-index.js

​	|-another-module.js



在another-module.js文件中可能有如下代码

```
import _ from 'lodash';
console.log(_.join(['Another','module','loaded!'],' '));
```

可以在webpack.config.js文件中为每个js文件创建一个入口

```
const path=require('path');
module.exports={
	mode:'development',
	entry:{
		index:'./src/index.js',
		another:'./src/another-module.js',
	},
	output:{
		filename:'[name].bundle.js',
		path:path.resolve(__didrname,'dist'),
	},
};
```

这样webpack就会为每个入口生成一个bundle文件。

但存在两个主要问题：

如果两个页面之间有共有的代码，那么这些代码会在每个bundle文件中都出现一次，导致代码重复

在进行手动配置时，如果应用有很多页面，那么可能需要写更多入口，而且不能动态地拆分代码

#### 防止重复prevent duplication

使用SplitChunksPlugin去重和分离代码块

```
module.exports{
	optimization:{
		splitChunks:{
			chunks:'all',
		},
	},
};
```

#### 动态导入dynamic imports

```
import(/* webpackChunkName:"lodash" */'loadsh').then(({default:_})=>{
	console.log(_.join(['Hello','webpack',' ']));
})
```

### 懒加载

也称延迟加载，也意味着延迟初始化对象，延迟计算值或者延迟加载文件，在webpack中，可以通过动态导入实现懒加载

```
import {add} from './math';
console.log(add(16,20));

import(/* webpackChunkName:"math" */ './math').then(({add})=>{
	console.log(add(16,26));
})
```

### 缓存

是另一种优化策略。webpack使用内容哈希。只有模块内容更改时才会改变内容哈希，从而利用好浏览器的缓存机制，提高网站加载速度，减少服务器负载

```
module.export={
	output:{
		filename:'[name].[contenthash].js',
	},
};
```



### Tree Shaking：消除无用代码

用于移除js上下文中的未引用代码。默认启用

```
//main.js
export function square(x){
	return x*x;
}
export function cube(x){
	return x*x*x;
}
```

```
//app.js
import {square} from './math.js'
console.log(square(5));
```

### Module Federation:跨项目资源共享

一个应用程序可以由多个独立的架构组成，这些架构之间不应该存在依赖关系，因此可以单独开发和部署，这个架构属于微前端

跨项目资源可以将模块分为本地模块和远程模块，本地模块时当前架构一部分，远程不属于，只是在运行时从容器加载

加载远程模块被视为异步操作。当使用远程模块时，这些异步操作将在下一个加载操作期间执行，位于远程模块和入口之间的代码块中。加载模块通常使用import函数调用

容器是由容器入口创建，入口公开了对特定模块的异步访问。公开访问的过程可以分为两步：

加载模块（异步）在代码块加载期间完成

执行模块（同步）在与其他模块交错执行期间完成

每个架构都可以充当容器

### 配置babel-loader

是一个将最新版本的js代码转换为向后兼容的旧版本js代码的工具。

安装

```
npm install -D babel-loader @babel/core @babel/present-env webpack
```

webpack配置示例

```
module:{
	rules:[]
		test: /\.js$/,  //匹配所有js文件
		exclude:/node_modules/,  //排除node_modules目录
		use:{
			loader:'babel-loader',//使用~处理这些文件
			options:{
				//可在这里设置label的配置选项
			}
		]
	}
}
```

可以使用options属性向loader传递选项

```
modules:{
	rules:[
		{
			test:/\.m?js$/,
			exclude:/(node_modules|bower_components)/,
			use:{
				loader:'babbel-loader',
				options:{
					presets:['@babel/present-env'],
					plugins:['@babel/plugin-proposal-object-reset-spread']
				}
			}
		}
	]
}
```

插件还支持以下loaderf特有的选项：

cacheDirectory：

cacheIdenttifier

cacheCompression：

customize：

1111111



### 自定义loader

提供了loader-builder工具函数，允许用户为每个经过babel处理的文件添加自定义处理选项。custom函数用于接收回调，将调用的loader的babel实例，确保了loader-builder工具函数能够使用与@babel/core相同的实例

如果不想直接调用.custom，可以向customize选项传入一个字符串，此字符串指向一个导出custom回调函数的文件

```
//从“./my-custom-loader.js”中导出，或者从任何想要的文件中导出
module.exports=require("babel-loader").custom(babel=>{
	function myPlugin(){
		return{
			visitor:{},
		};
	}
	return{
		customOptions({opt1,opt2,...loader}){
			return{
				custom:{opt1,opt2},
				loader,
			};
		},
		config(cfg){
			if(cfg.hasFilesystemConfig()){
				return cfg.options;
			}
			return{
				...cfg.options,
				plugins:{
					...(cfg.options.plugin || []),
					myPlugin,
				},
			};
		},
		result(result){
			return{
				...result,
				code:result.code+"\n//自定义loader生成",
			};
		},
	};
});
```




然后在webpack config文件中添加以下内容：

```
modules.exports={
	...
	module:{
		rules:[{
			...
			loader:path.join(__dirname,'my-custom-loader.js'),
		}]
	}
}
```

customOptions(options:Object)：该函数接收一个options对象，从babel-loader的选项中分离出自定义选项，返回一个包含custom和loader两个属性的对象

config（cfg：PartialConfig）：接收一个指定的babel的PartialConfig对象，返回一个应该被传递给babel.transform的option对象

result（result:Result)：该函数接收一个指定的babel结果对象，允许loader是对他进行额外调整

### 注意事项

11111111111



## 使用webpack配置vue项目

```
mkdir vue-webpack-project
cd vue-webpack-project
npm init -y

```

```
PS D:\vue3学习\vue-webpack-project> npm init -y
Wrote to D:\vue3学习\vue-webpack-project\package.json:

{
  "name": "vue-webpack-project",
  "version": "1.0.0",
  "main": "webpack.config.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "description": ""
}
```

npm install vue webpack webpack-cli --save-dev

### 配置loader和plugin

根目录下创建webpack-config.js文件

这是配置文件。首先需要引入webpack和vueloaderplugin

const VueLoaderPlugin =require('vue-loader/lib/plugin');

const path=require('path')

module.exports={

...

};

接下来配置loader和plugin。在module.exports对象中添加以下内容

```
module.exports={
	modules:{
		rules:[
			{
				test:/\.vue$/,
				loader:'vue-loader'
			},
			{
				test:/\.js$/,
				loader:'babel-loader'
			},
			{
				test:/\.css$/,
				use:[
					'vue-style-loader',
					'css-loader'
				]
			}
		]
	},
	plugins:[
		new VueLoaderPlugin()
	],
	resolve:{
		alias:{
			'vue$':'vue/dist/vue.esm.js'
		},
		extensions:['*','.js','.vue','.json']
	},
};
```

### 设置环境变量和模式

为了区分开发模式和生产环境，在webpack.config.js中添加以下内容：

```
const isProduction=process.env.NODE_ENV==='production';
module.exports={
	mode:isProduction ? 'production' : 'development',
}
```

通过设置NODE_ENV环境变量来切换开发模式和生产模式，development是开发模式，product是生产模式

### 实现代码拆分和懒加载

```
optimization:{
        splitChunks:{
            chunks:'all'
        }
    },
```

在vue组件中使用import函数实现懒加载：

```
const MyComponent=()=>import('./MyComponent.vue');
```

### 使用vue.config.js管理webpack

```
module.exports={
    configureWebpack:config=>{
        configureWebpack:config=>{
            if(process.env.NODE_ENV==='production'){
                //为生产环境修改配置
            }
            else{
                //为开发环境修改配置
            }
        }
    }
}
```

# 搭建后台模拟环境

## postman的安装与使用

是一款旨在帮助开发人员更快速开发api的工具

允许用户发送任何类型的http请求，可以更方便地自定义参数和http头

输出自动按照语法格式高亮显示并给出语法解析结果，目前支持常见的语法包括html、json、xml

![image-20260325171042854](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260325171042854.png)

## json-server的安装与使用

是一个开源框架，可以在不写一句代码的情况下实现Rest API

npm install -g json-server

```
PS D:\vue3学习> json-server data.json

  \{^_^}/ hi!

  Loading data.json
  Oops, data.json doesn't seem to exist
  Creating data.json with some default data

  Done

  Resources
  http://localhost:3000/posts
  http://localhost:3000/comments
  http://localhost:3000/profile

  Home
  http://localhost:3000

  Type s + enter at any time to create a snapshot of the database
```

```
 D:\vue3学习> json-server --watch --port 8100 data.json

  \{^_^}/ hi!

  Loading data.json
  Done

  Resources
  http://localhost:8100/posts
  http://localhost:8100/comments
  http://localhost:8100/profile

  Home
  http://localhost:8100

  Type s + enter at any time to create a snapshot of the database
  Watching...

```

![image-20260325171631894](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260325171631894.png)

然后使用postman测试生成的接口是否可以正常使用

![image-20260325171935574](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260325171935574.png)

## 通过json-server实现增删改查操作

建立和配置项目

npm create vue@3

配置仅勾选typescript

npm install axios -save

npm install element-plus --save

修改main.ts

```
import './assets/main.css'
import 'element-plus/dist/index.css'
import ElementPlus from 'element-plus'
import { createApp } from 'vue'
import App from './App.vue'
import router from './router'

const app = createApp(App)

app.use(router)
app.use(ElementPlus)
app.mount('#app')

```

新建data.json

```
{
    "users":[
        {
            "id":1,
            "name":"张三",
            "age":18,
            "address":"北京市海淀区"
        },
        {
            "id":2,
            "name":"李四",
            "age":20,
            "address":"天津市河西区"
        }
           ]
}
```

执行命令

json-sever data.json

```
PS D:\vue3学习\RouterDemo2> json-server data.json

  \{^_^}/ hi!

  Loading data.json
  Done

  Resources
  http://localhost:3000/users

  Home
  http://localhost:3000

  Type s + enter at any time to create a snapshot of the database
GET /users 200 13.175 ms - 192
```

基本配置如创建项目、引入ui框架和数据源已经实现了

### 查询与删除数据

新建UserTable.vue文件

```
<template>
  <div>
    <!-- 添加用户 -->
    <el-form class="form-div" :model="form" label-width="80px">
      <el-form-item label="姓名">
        <el-input v-model="form.name" />
      </el-form-item>
      <el-form-item label="年龄">
        <el-input-number v-model="form.age" />
      </el-form-item>
      <el-form-item label="地址">
        <el-input v-model="form.address" />
      </el-form-item>
      <el-form-item>
        <el-button type="primary" @click="addUser">添加用户</el-button>
      </el-form-item>
    </el-form>

    <!-- 用户表格 -->
    <el-table :data="users" style="width: 100%; margin-top: 20px;">
      <el-table-column prop="id" label="ID" align="center" width="50" />
      <el-table-column prop="name" label="姓名" width="100" />
      <el-table-column prop="age" label="年龄" width="100" />
      <el-table-column prop="address" label="地址" width="150" />
      <el-table-column label="操作" width="150">
        <template #default="{ row }">
          <el-button type="primary" @click="showEditDialog(row)">编辑</el-button>
          <el-button type="danger" @click="deleteUser(row)">删除</el-button>
        </template>
      </el-table-column>
    </el-table>

    <!-- 编辑用户对话框 -->
    <el-dialog title="编辑用户" v-model="editDialogVisible">
      <el-form :model="editForm" label-width="80px">
        <el-form-item label="姓名">
          <el-input v-model="editForm.name" />
        </el-form-item>
        <el-form-item label="年龄">
          <el-input-number v-model="editForm.age" />
        </el-form-item>
        <el-form-item label="地址">
          <el-input v-model="editForm.address" />
        </el-form-item>
      </el-form>
      <template #footer>
        <span class="dialog-footer">
          <el-button @click="editDialogVisible = false">取消</el-button>
          <el-button type="primary" @click="updateUser">确定</el-button>
        </span>
      </template>
    </el-dialog>

    <!-- 删除确认弹窗 -->
    <el-dialog
      v-model="deleteDialogVisible"
      title="确认删除"
      width="30%"
    >
      <span>确定要删除该用户吗？</span>
      <template #footer>
        <el-button @click="deleteDialogVisible = false">取消</el-button>
        <el-button type="danger" @click="confirmDeleteUser">确认删除</el-button>
      </template>
    </el-dialog>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'
import axios from 'axios'
import { ElMessage } from 'element-plus'

// 定义类型
interface User {
  id: number
  name: string
  age: number
  address: string
}

interface EditForm {
  id: number | null
  name: string
  age: number | null
  address: string
}

export default defineComponent({
  setup() {
    // 所有变量 & 方法 必须写在 setup 内部
    const users = ref<User[]>([])
    
    // 添加表单
    const form = ref<EditForm>({
      id: null,
      name: '',
      age: null,
      address: ''
    })

    // 编辑弹窗
    const editDialogVisible = ref(false)
    const editForm = ref<EditForm>({
      id: null,
      name: '',
      age: null,
      address: ''
    })

    // 删除弹窗
    const deleteDialogVisible = ref(false)
    const userToDelete = ref<User | null>(null)

    // 表单验证
    const isFormValid = (form: EditForm) => {
      return form.name.trim() !== '' && form.age !== null && form.address.trim() !== ''
    }

    // 获取用户列表
    const fetchUsers = async () => {
      const res = await axios.get<User[]>('http://localhost:3000/users')
      users.value = res.data
    }

    // 添加用户
    const addUser = async () => {
      if (!isFormValid(form.value)) {
        ElMessage.error('请输入完整信息')
        return
      }
      const res = await axios.post('http://localhost:3000/users', form.value)
      users.value.push(res.data)
      
      // 清空表单
      form.value = { id: null, name: '', age: null, address: '' }
      ElMessage.success('添加成功')
    }

    // 打开编辑弹窗
    const showEditDialog = (user: User) => {
      editDialogVisible.value = true
      editForm.value = { ...user }
    }

    // 更新用户
    const updateUser = async () => {
      if (!isFormValid(editForm.value)) {
        ElMessage.error('请输入完整信息')
        return
      }

      const id = editForm.value.id
      if (!id) return

      const res = await axios.put<User>(`http://localhost:3000/users/${id}`, editForm.value)
      
      // 更新列表数据
      const index = users.value.findIndex(item => item.id === id)
      if (index !== -1) {
        users.value[index] = res.data
      }

      editDialogVisible.value = false
      ElMessage.success('修改成功')
    }

    // 删除用户（打开弹窗）
    const deleteUser = (user: User) => {
      deleteDialogVisible.value = true
      userToDelete.value = user
    }

    // 确认删除
    const confirmDeleteUser = async () => {
      if (!userToDelete.value) return
      
      const id = userToDelete.value.id
      await axios.delete(`http://localhost:3000/users/${id}`)
      
      // 更新列表
      users.value = users.value.filter(u => u.id !== id)
      deleteDialogVisible.value = false
      ElMessage.success('删除成功')
    }

    // 初始化加载数据
    fetchUsers()

    // 必须 return 出去才能在 template 使用
    return {
      users,
      form,
      addUser,
      editDialogVisible,
      editForm,
      showEditDialog,
      updateUser,
      deleteDialogVisible,
      deleteUser,
      confirmDeleteUser
    }
  }
})
</script>

<style scoped>
.form-div {
  margin-top: 16px;
}
.dialog-footer {
  text-align: right;
}
</style>
```

UserInfo.vue

```
<template>
    <div>
        <el-table :data="users" style="width: 100%">
            <el-table-column prop="id" label="ID" align="center" width="50" />
            <el-table-column prop="name" label="姓名"width="100" />
            <el-table-column prop="age" label="年龄"width="100" />
            <el-table-column prop="address" label="地址"width="150" />
            <el-table-column label="操作" width="150">
                <template #default="{ row }">
                    <el-button type="primary" @click="showEditDialog(row)">编辑</el-button>
                    <el-button type="danger" @click="deleteUser(row)">删除</el-button>
                </template>
            </el-table-column>
        </el-table>
    </div>
</template>
<script lang="ts">
    import {ElMessage} from 'element-plus'
    import {defineComponent,ref} from 'vue'
    import axios from 'axios'
    interface User{
        id:number,
        name:string,
        age:number,
        address:string
    }
    interface EditForm{
        id:number | null,
        name:string,
        age:number | null,
        address:string
    }
    export default defineComponent({
        setup() {
          const users=ref<User[]>([]);
          const deleteDialogVisible=ref(false);
          const userToDelete=ref<User | null>(null);
          const fetchUsers=async()=>{
            const response=await axios.get<User[]>('http://localhost:3000/users');
            users.value=response.data;
          }
          const deleteUser=(user: User)=>{
            deleteDialogVisible.value=true;
            userToDelete.value=user;
          }
          const confirmDeleteUser=async()=>{
            if(!userToDelete.value){
                await axios.delete(`http://localhost:3000/users/${userToDelete.value.id}`);
                users.value=users.value.filter(u=>u.id!==userToDelete.value.id);
                deleteDialogVisible.value=false;
            }
          }
          fetchUsers();
          return{
            users,
            deleteUser,
            deleteDialogVisible,
            confirmDeleteUser,
          }
        },
    })
</script>
<style scoped>
    .form-div{
        margin-top:16px;
    }
</style>

```

App.vue

```
<script lang="ts">
import { defineComponent } from 'vue'
import UserTable from './views/UserTable.vue'

export default defineComponent({
  components: {
    UserTable
  }
})
</script>

<template>
  <div id="app">
    <user-table />
  </div>
</template>

<style>
#app {
  padding: 2rem;
  max-width: 1200px;
  margin: 0 auto;
}
</style>
```

![image-20260325200245842](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260325200245842.png)

![image-20260325200231337](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260325200231337.png)

![image-20260325200437992](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260325200437992.png)

![image-20260325200447203](C:/Users/10126/AppData/Roaming/Typora/typora-user-images/image-20260325200447203.png)

# 项目实战一：商城后台管理系统--项目设计与框架搭建

商城后台管理：

用户管理：注册登录、权限管理

消息管理：消息分类查询、意见反馈管理

系统设置：主题切换、字体设置、全屏模式

资产盘点：资产概况、数据分析

商品管理：商品查询、商品添加、商品编辑

订单管理：订单查询

库存管理：库存查询、库存编辑

## 项目起步

### 框架选型

使用vue-element-plus-admin

如果存在兼容性问题切换版本

node 18.15.0

npm 9.5.0

pnpm 8.6.3

vue 3.2.7

vue-router 4.1.6

vite 4.2.1

axios 1.3.5

element-plus 2.3.3

echarts 5.4.2

在ui模式库中，选择使用element-plus进行开发

这个而项目目录下有很多文件

```
.
├── .github # github workflows 相关
├── .husky # husky 配置
├── .vscode # vscode 配置
├── mock # 自定义 mock 数据及配置
├── public # 静态资源
├── src # 项目代码
│   ├── api # api接口管理
|   |── axios # axios配置
│   ├── assets # 静态资源
│   ├── components # 公用组件
│   ├── constants # 存放常量
│   ├── hooks # 常用hooks
│   ├── layout # 布局组件
│   ├── locales # 语言文件
│   ├── plugins # 外部插件
│   ├── router # 路由配置
│   ├── store # 状态管理
│   ├── styles # 全局样式
│   ├── utils # 全局工具类
│   ├── views # 路由页面
│   ├── App.vue # 入口vue文件
│   ├── main.ts # 主入口文件
│   └── permission.ts # 路由拦截
├── types # 全局类型
├── .env.base # 本地开发环境 环境变量配置
├── .env.dev # 打包到开发环境 环境变量配置
├── .env.gitee # 针对 gitee 的环境变量 可忽略
├── .env.pro # 打包到生产环境 环境变量配置
├── .env.test # 打包到测试环境 环境变量配置
├── .eslintignore # eslint 跳过检测配置
├── .eslintrc.js # eslint 配置
├── .gitignore # git 跳过配置
├── .prettierignore # prettier 跳过检测配置
├── .stylelintignore # stylelint 跳过检测配置
├── .versionrc 自动生成版本号及更新记录配置
├── CHANGELOG.md # 更新记录
├── commitlint.config.js # git commit 提交规范配置
├── index.html # 入口页面
├── package.json
├── .postcssrc.js # postcss 配置
├── prettier.config.js # prettier 配置
├── README.md # 英文 README
├── README.zh-CN.md # 中文 README
├── stylelint.config.js # stylelint 配置
├── tsconfig.json # typescript 配置
├── vite.config.ts # vite 配置
└── uno.config.ts # unocss 配置
```

本地环境需要安装 [Pnpm](https://pnpm.io/)、[Node.js](http://nodejs.org/) 和 [Git](https://git-scm.com/)

### 从 GitHub 获取代码

```
# clone 代码
git clone https://github.com/kailong321200875/vue-element-plus-admin.git
```

### 从 Gitee 获取代码

```
git clone https://gitee.com/kailong110120130/vue-element-plus-admin.git
```



### 创建项目

创建项目之前，先打开package.json，查看有哪些运行命令

安装pnpm。这个工具是pnpm替代者，不仅运行速度更快，而且节约磁盘空间

```
# 全局安装 pnpm
npm i -g pnpm

# 验证
pnpm -v
```

然后再

```
# clone 代码
git clone https://github.com/kailong321200875/vue-element-plus-admin.git
//安装依赖
pnpm -i
//运行项目
npm run dev

```

中文配置router部分举例：

```
export default{
	...
	router:{
		login:'登录',
		level:'多级菜单',
		menu:'菜单'，
		...
	}
}
```

加入在router部分需要用到一些文本，如登录、多级菜单和菜单等，可以在这些配置文件中使用一个固定的Key标识来表示这些文本，如login、level和menu等。对于同一个标识，不同语言的配置文件会写上相应语言的文本，如中文配置login:'登录',英文配置中login:'Login'，用户选择不同语言就可以看到对应文本，完成了国际化。

打开src/router/index.ts

```
{
    path: '/login',
    component: () => import('@/views/Login/Login.vue'),
    name: 'Login',
    meta: {
      hidden: true,
      title: t('router.login'),
      noTagsView: true
    }
```

title后面有一个t，t是多语言I18n的一个方法。t方法中的router.login就是在语言配置文件中的Key。当加载中文的时候会显示“登录”，加载英文时显示Login

### 自动导入组件

unplugin-vue-components可以实现组建的自动化导入，市面上成熟的框架一般都会自带

### 封装网络请求

为了解决以下问题

统一请求地址

```

```

