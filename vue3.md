# Vue3快速上手

<img src="https://user-images.githubusercontent.com/499550/93624428-53932780-f9ae-11ea-8d16-af949e16a09f.png" style="width:200px" />



## 1.Vue3简介

- 2020年9月18日，Vue.js发布3.0版本，代号：One Piece（海贼王）
- 耗时2年多、[2600+次提交](https://github.com/vuejs/vue-next/graphs/commit-activity)、[30+个RFC](https://github.com/vuejs/rfcs/tree/master/active-rfcs)、[600+次PR](https://github.com/vuejs/vue-next/pulls?q=is%3Apr+is%3Amerged+-author%3Aapp%2Fdependabot-preview+)、[99位贡献者](https://github.com/vuejs/vue-next/graphs/contributors) 
- github上的tags地址：https://github.com/vuejs/vue-next/releases/tag/v3.0.0

## 2.Vue3带来了什么

### 1.性能的提升

- 打包大小减少41%

- 初次渲染快55%, 更新渲染快133%

- 内存减少54%

  ......

### 2.源码的升级

- 使用Proxy代替defineProperty实现响应式

- 重写虚拟DOM的实现和Tree-Shaking

  ......

### 3.拥抱TypeScript

- Vue3可以更好的支持TypeScript

### 4.新的特性

1. Composition API（组合API）

   - setup配置
   - ref与reactive
   - watch与watchEffect
   - provide与inject
   - ......
2. 新的内置组件
   - Fragment 
   - Teleport
   - Suspense
3. 其他改变

   - 新的生命周期钩子
   - data 选项应始终被声明为一个函数
   - 移除keyCode支持作为 v-on 的修饰符
   - ......

# 一、创建Vue3.0工程

## 1.使用 vue-cli 创建

官方文档：https://cli.vuejs.org/zh/guide/creating-a-project.html#vue-create

```bash
## 查看@vue/cli版本，确保@vue/cli版本在4.5.0以上
vue --version
## 安装或者升级你的@vue/cli
npm install -g @vue/cli
## 创建
vue create vue_test
## 启动
cd vue_test
npm run serve
```

## 2.使用 vite 创建

官方文档：https://v3.cn.vuejs.org/guide/installation.html#vite

vite官网：https://vitejs.cn

- 什么是vite？—— 新一代前端构建工具。
- 优势如下：
  - 开发环境中，无需打包操作，可快速的冷启动。
  - 轻量快速的热重载（HMR）。
  - 真正的按需编译，不再等待整个应用编译完成。
- 传统构建 与 vite构建对比图

<figure class="svg-image-root"><svg viewBox="0 0 1896 1071" fill="none" xmlns="http://www.w3.org/2000/svg">
<text fill="#FFAA3E" xml:space="preserve" style="white-space: pre" font-size="80" letter-spacing="0em"><tspan x="46" y="132.344">Bundle based dev server</tspan></text>
<rect x="48" y="239" width="1086" height="767" rx="98" stroke="#FFC36B" stroke-width="4"></rect>
<rect x="108" y="577" width="212" height="83" rx="10" fill="#C3E88C"></rect>
<text fill="#15505C" xml:space="preserve" style="white-space: pre" font-size="38" font-weight="600" letter-spacing="0em"><tspan x="170" y="631.488">entry</tspan></text>
<rect x="476" y="712" width="212" height="88" rx="10" fill="#4FC08D"></rect>
<text fill="#15505C" xml:space="preserve" style="white-space: pre" font-size="38" font-weight="600" letter-spacing="0.33em"><tspan x="552.5" y="768.988">···</tspan></text>
<rect x="476" y="438" width="212" height="88" rx="10" fill="#4FC08D"></rect>
<text fill="#15505C" xml:space="preserve" style="white-space: pre" font-size="38" font-weight="600" letter-spacing="0em"><tspan x="537" y="494.988">route</tspan></text>
<rect x="473" y="576" width="212" height="88" rx="10" fill="#4FC08D"></rect>
<text fill="#15505C" xml:space="preserve" style="white-space: pre" font-size="38" font-weight="600" letter-spacing="0em"><tspan x="534" y="632.988">route</tspan></text>
<path d="M472.614 481.699L438.815 489.291L462.289 514.766L472.614 481.699ZM324.582 622.18L454.791 502.201L450.726 497.789L320.516 617.768L324.582 622.18Z" fill="#E06666"></path>
<path d="M469 620L439 602.679V637.321L469 620ZM323 623H442V617H323V623Z" fill="#E06666"></path>
<path d="M472.614 756.105L462.032 723.12L438.757 748.777L472.614 756.105ZM320.533 622.196L450.601 740.186L454.632 735.742L324.565 617.752L320.533 622.196Z" fill="#E06666"></path>
<path d="M822.052 905.098L815.036 871.175L789.166 894.213L822.052 905.098ZM689.041 760.243L801.856 886.929L806.337 882.939L693.521 756.253L689.041 760.243Z" fill="#FFC36B"></path>
<path d="M819.908 756.105L811.894 722.403L786.715 746.195L819.908 756.105ZM689.1 622.034L799.185 738.54L803.546 734.419L693.462 617.914L689.1 622.034Z" fill="#FFC36B"></path>
<path d="M817.765 623.19L788.215 605.112L787.334 639.742L817.765 623.19ZM691.205 622.973L790.697 625.502L790.85 619.504L691.357 616.975L691.205 622.973Z" fill="#FFC36B"></path>
<path d="M818.837 481.699L789.286 463.622L788.406 498.252L818.837 481.699ZM692.277 481.483L791.769 484.012L791.922 478.014L692.429 475.485L692.277 481.483Z" fill="#FFC36B"></path>
<path d="M819.909 340.209L786.924 350.795L812.584 374.067L819.909 340.209ZM696.719 480.499L803.992 362.224L799.547 358.193L692.275 476.468L696.719 480.499Z" fill="#FFC36B"></path>
<path d="M817.765 614.614L810.467 580.751L784.789 604.002L817.765 614.614ZM692.273 480.497L797.418 596.614L801.866 592.587L696.721 476.47L692.273 480.497Z" fill="#FFC36B"></path>
<rect x="822" y="288" width="212" height="88" rx="10" fill="#4FC08D"></rect>
<text fill="#15505C" xml:space="preserve" style="white-space: pre" font-size="38" font-weight="600" letter-spacing="0em"><tspan x="864" y="344.988">module</tspan></text>
<rect x="822" y="435" width="212" height="87" rx="10" fill="#4FC08D"></rect>
<text fill="#15505C" xml:space="preserve" style="white-space: pre" font-size="38" font-weight="600" letter-spacing="0em"><tspan x="864" y="491.488">module</tspan></text>
<rect x="820" y="571" width="212" height="88" rx="10" fill="#4FC08D"></rect>
<text fill="#15505C" xml:space="preserve" style="white-space: pre" font-size="38" font-weight="600" letter-spacing="0em"><tspan x="862" y="627.988">module</tspan></text>
<rect x="822" y="718" width="212" height="87" rx="10" fill="#4FC08D"></rect>
<text fill="#15505C" xml:space="preserve" style="white-space: pre" font-size="38" font-weight="600" letter-spacing="0em"><tspan x="864" y="774.488">module</tspan></text>
<rect x="822" y="864" width="212" height="88" rx="10" fill="#4FC08D"></rect>
<text fill="#15505C" xml:space="preserve" style="white-space: pre" font-size="38" font-weight="600" letter-spacing="0.33em"><tspan x="898.5" y="920.988">···</tspan></text>
<path d="M1239 627L1209 609.679V644.321L1239 627ZM1136 630H1212V624H1136V630Z" fill="#FFC36B"></path>
<path d="M1596 627L1566 609.679V644.321L1596 627ZM1493 630H1569V624H1493V630Z" fill="#FFC36B"></path>
<rect x="1239" y="545" width="254" height="144" rx="10" fill="#C692EA"></rect>
<text fill="white" xml:space="preserve" style="white-space: pre" font-size="38" font-weight="600" letter-spacing="0em"><tspan x="1306.5" y="629.988">Bundle</tspan></text>
<rect x="1596" y="543" width="254" height="143" rx="10" fill="#009688"></rect>
<text fill="white" xml:space="preserve" style="white-space: pre" font-size="38" font-weight="600" letter-spacing="0em"><tspan x="1667.71" y="604.988">Server
</tspan><tspan x="1675.76" y="649.988">ready</tspan></text>
</svg>
</figure>
<figure class="svg-image-root"><svg viewBox="0 0 1896 1071" fill="none" xmlns="http://www.w3.org/2000/svg">
<text fill="#FFAA3E" xml:space="preserve" style="white-space: pre" font-size="80" letter-spacing="0em"><tspan x="45" y="129.344">Native ESM based dev server</tspan></text>
<rect x="632" y="526" width="273" height="106" rx="10" fill="#C3E88C"></rect>
<text fill="#15505C" xml:space="preserve" style="white-space: pre" font-size="38" font-weight="600" letter-spacing="0em"><tspan x="724.5" y="591.988">entry</tspan></text>
<rect x="1106" y="699" width="274" height="114" rx="10" fill="#666665"></rect>
<g filter="url(#filter0_d_5_61)">
<text fill="#CCCCCB" xml:space="preserve" style="white-space: pre" font-size="38" font-weight="600" letter-spacing="0.33em"><tspan x="1213.5" y="768.988">···</tspan></text>
</g>
<rect x="1106" y="346" width="274" height="113" rx="10" fill="#4FC08D"></rect>
<text fill="#15505C" xml:space="preserve" style="white-space: pre" font-size="38" font-weight="600" letter-spacing="0em"><tspan x="1198" y="415.488">route</tspan></text>
<rect x="1102" y="524" width="273" height="114" rx="10" fill="#666665"></rect>
<text fill="#CCCCCB" xml:space="preserve" style="white-space: pre" font-size="38" font-weight="600" letter-spacing="0em"><tspan x="1193.5" y="593.988">route</tspan></text>
<path d="M1101.79 402.463L1067.99 410.054L1091.46 435.529L1101.79 402.463ZM910.168 583.106L1083.96 422.965L1079.9 418.553L906.102 578.693L910.168 583.106Z" fill="#C892E9"></path>
<path d="M1097 581L1067 563.679V598.321L1097 581ZM908 584H1070V578H908V584Z" fill="#999899"></path>
<path d="M1101.79 756.57L1091.2 723.584L1067.93 749.242L1101.79 756.57ZM906.119 583.121L1079.77 740.651L1083.8 736.207L910.151 578.677L906.119 583.121Z" fill="#999899"></path>
<path d="M1552.72 948.839L1545.7 914.916L1519.83 937.953L1552.72 948.839ZM1381.73 761.331L1532.52 930.67L1537 926.68L1386.21 757.341L1381.73 761.331Z" fill="#999899"></path>
<path d="M1549.95 756.569L1541.94 722.868L1516.76 746.659L1549.95 756.569ZM1381.79 582.96L1529.23 739.005L1533.59 734.884L1386.15 578.839L1381.79 582.96Z" fill="#999899"></path>
<path d="M1547.19 585.049L1517.64 566.972L1516.76 601.602L1547.19 585.049ZM1383.89 583.898L1520.12 587.362L1520.27 581.364L1384.04 577.9L1383.89 583.898Z" fill="#999899"></path>
<path d="M1548.57 402.463L1519.02 384.386L1518.14 419.015L1548.57 402.463ZM1385.27 401.312L1521.5 404.776L1521.66 398.778L1385.43 395.314L1385.27 401.312Z" fill="#C892E9"></path>
<path d="M631.489 585.049L601.583 567.567L601.396 602.207L631.489 585.049ZM375.576 586.666L604.473 587.903L604.506 581.903L375.608 580.666L375.576 586.666Z" fill="#C892E9"></path>
<path d="M1549.95 219.877L1516.97 230.462L1542.63 253.735L1549.95 219.877ZM1390.34 400.329L1534.04 241.892L1529.59 237.861L1385.89 396.298L1390.34 400.329Z" fill="#C892E9"></path>
<path d="M1547.19 573.983L1539.89 540.12L1514.21 563.372L1547.19 573.983ZM1385.89 400.327L1526.84 555.983L1531.29 551.956L1390.34 396.3L1385.89 400.327Z" fill="#C892E9"></path>
<rect x="1553" y="152" width="274" height="113" rx="10" fill="#4FC08D"></rect>
<text fill="#15505C" xml:space="preserve" style="white-space: pre" font-size="38" font-weight="600" letter-spacing="0em"><tspan x="1626" y="221.488">module</tspan></text>
<rect x="1553" y="341" width="274" height="114" rx="10" fill="#4FC08D"></rect>
<text fill="#15505C" xml:space="preserve" style="white-space: pre" font-size="38" font-weight="600" letter-spacing="0em"><tspan x="1621.5" y="411.818">module</tspan></text>
<rect x="1550" y="517" width="274" height="114" rx="10" fill="#666665"></rect>
<text fill="#CCCCCB" xml:space="preserve" style="white-space: pre" font-size="38" font-weight="600" letter-spacing="0em"><tspan x="1623" y="586.988">module</tspan></text>
<rect x="1553" y="707" width="274" height="113" rx="10" fill="#666665"></rect>
<text fill="#CCCCCB" xml:space="preserve" style="white-space: pre" font-size="38" font-weight="600" letter-spacing="0em"><tspan x="1626" y="776.488">module</tspan></text>
<rect x="1553" y="896" width="274" height="113" rx="10" fill="#666665"></rect>
<text fill="#CCCCCB" xml:space="preserve" style="white-space: pre" font-size="38" font-weight="600" letter-spacing="0.33em"><tspan x="1660.5" y="965.488">···</tspan></text>
<rect x="45" y="491" width="330" height="179" rx="10" fill="#029788"></rect>
<text fill="white" xml:space="preserve" style="white-space: pre" font-size="38" font-weight="600" letter-spacing="0em"><tspan x="154.707" y="570.988">Server
</tspan><tspan x="162.76" y="615.988">ready</tspan></text>
<line x1="507.615" y1="459.201" x2="506.232" y2="569.859" stroke="#C892E9" stroke-width="4" stroke-dasharray="8 8"></line>
<line x1="1038.78" y1="733.073" x2="1037.37" y2="883.845" stroke="#E06666" stroke-width="4" stroke-dasharray="8 8"></line>
<text fill="#E06666" xml:space="preserve" style="white-space: pre" font-size="38" letter-spacing="0em"><tspan x="918" y="938.988">Dynamic import
</tspan><tspan x="918" y="983.988">(code split point)</tspan></text>
<text fill="#C892E9" xml:space="preserve" style="white-space: pre" font-size="38" letter-spacing="0em"><tspan x="399" y="431.488">HTTP request</tspan></text>
<defs>
<filter id="filter0_d_5_61" x="1212.15" y="752.766" width="60.9863" height="13.2324" filterUnits="userSpaceOnUse" color-interpolation-filters="sRGB">
<feFlood flood-opacity="0" result="BackgroundImageFix"></feFlood>
<feColorMatrix in="SourceAlpha" type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 127 0" result="hardAlpha"></feColorMatrix>
<feOffset dy="4"></feOffset>
<feGaussianBlur stdDeviation="2"></feGaussianBlur>
<feComposite in2="hardAlpha" operator="out"></feComposite>
<feColorMatrix type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0.25 0"></feColorMatrix>
<feBlend mode="normal" in2="BackgroundImageFix" result="effect1_dropShadow_5_61"></feBlend>
<feBlend mode="normal" in="SourceGraphic" in2="effect1_dropShadow_5_61" result="shape"></feBlend>
</filter>
</defs>
</svg>
</figure>

```bash
## 创建工程
npm init vite-app <project-name>
## 进入工程目录
cd <project-name>
## 安装依赖
npm install
## 运行
npm run dev
```

# 二、常用 Composition API

官方文档: https://v3.cn.vuejs.org/guide/composition-api-introduction.html

## 1.拉开序幕的setup

1. 理解：Vue3.0中一个新的配置项，值为一个函数。
2. setup是所有<strong style="color:#DD5145">Composition API（组合API）</strong><i style="color:gray;font-weight:bold">“ 表演的舞台 ”</i>。
4. 组件中所用到的：数据、方法等等，均要配置在setup中。
5. setup函数的两种返回值：
   1. 若返回一个对象，则对象中的属性、方法, 在模板中均可以直接使用。（重点关注！）
   2. <span style="color:#aad">若返回一个渲染函数：则可以自定义渲染内容。（了解）</span>
6. 注意点：
   1. 尽量不要与Vue2.x配置混用
      - Vue2.x配置（data、methos、computed...）中<strong style="color:#DD5145">可以访问到</strong>setup中的属性、方法。
      - 但在setup中<strong style="color:#DD5145">不能访问到</strong>Vue2.x配置（data、methos、computed...）。
      - 如果有重名, setup优先。
   2. setup不能是一个async函数，因为返回值不再是return的对象, 而是promise, 模板看不到return对象中的属性。（后期也可以返回一个Promise实例，但需要Suspense和异步组件的配合）

##  2.ref函数

- 作用: 定义一个响应式的数据
- 语法: ``const xxx = ref(initValue)`` 
  - 创建一个包含响应式数据的<strong style="color:#DD5145">引用对象（reference对象，简称ref对象）</strong>。
  - JS中操作数据： ``xxx.value``
  - 模板中读取数据: 不需要.value，直接：``<div>{{xxx}}</div>``
- 备注：
  - 接收的数据可以是：基本类型、也可以是对象类型。
  - 基本类型的数据：响应式依然是靠``Object.defineProperty()``的``get``与``set``完成的。
  - 对象类型的数据：内部 <i style="color:gray;font-weight:bold">“ 求助 ”</i> 了Vue3.0中的一个新函数—— ``reactive``函数。

## 3.reactive函数

- 作用: 定义一个<strong style="color:#DD5145">对象类型</strong>的响应式数据（基本类型不要用它，要用``ref``函数）
- 语法：``const 代理对象= reactive(源对象)``接收一个对象（或数组），返回一个<strong style="color:#DD5145">代理对象（Proxy的实例对象，简称proxy对象）</strong>
- reactive定义的响应式数据是“深层次的”。
- 内部基于 ES6 的 Proxy 实现，通过代理对象操作源对象内部数据进行操作。

## 4.Vue3.0中的响应式原理

### vue2.x的响应式

- 实现原理：
  - 对象类型：通过``Object.defineProperty()``对属性的读取、修改进行拦截（数据劫持）。
  
  - 数组类型：通过重写更新数组的一系列方法来实现拦截。（对数组的变更方法进行了包裹）。
  
    ```js
    Object.defineProperty(data, 'count', {
        get () {}, 
        set () {}
    })
    ```

- 存在问题：
  - 新增属性、删除属性, 界面不会更新。
  - 直接通过下标修改数组, 界面不会自动更新。

### Vue3.0的响应式

- 实现原理: 
  - 通过Proxy（代理）:  拦截对象中任意属性的变化, 包括：属性值的读写、属性的添加、属性的删除等。
  - 通过Reflect（反射）:  对源对象的属性进行操作。
  - MDN文档中描述的Proxy与Reflect：
    - Proxy：https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Proxy
    
    - Reflect：https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Reflect
    
      ```js
      new Proxy(data, {
      	// 拦截读取属性值
          get (target, prop) {
          	return Reflect.get(target, prop)
          },
          // 拦截设置属性值或添加新属性
          set (target, prop, value) {
          	return Reflect.set(target, prop, value)
          },
          // 拦截删除属性
          deleteProperty (target, prop) {
          	return Reflect.deleteProperty(target, prop)
          }
      })
      
      proxy.name = 'tom'   
      ```

## 5.reactive对比ref

-  从定义数据角度对比：
   -  ref用来定义：<strong style="color:#DD5145">基本类型数据</strong>。
   -  reactive用来定义：<strong style="color:#DD5145">对象（或数组）类型数据</strong>。
   -  备注：ref也可以用来定义<strong style="color:#DD5145">对象（或数组）类型数据</strong>, 它内部会自动通过``reactive``转为<strong style="color:#DD5145">代理对象</strong>。
-  从原理角度对比：
   -  ref通过``Object.defineProperty()``的``get``与``set``来实现响应式（数据劫持）。
   -  reactive通过使用<strong style="color:#DD5145">Proxy</strong>来实现响应式（数据劫持）, 并通过<strong style="color:#DD5145">Reflect</strong>操作<strong style="color:orange">源对象</strong>内部的数据。
-  从使用角度对比：
   -  ref定义的数据：操作数据<strong style="color:#DD5145">需要</strong>``.value``，读取数据时模板中直接读取<strong style="color:#DD5145">不需要</strong>``.value``。
   -  reactive定义的数据：操作数据与读取数据：<strong style="color:#DD5145">均不需要</strong>``.value``。

## 6.setup的两个注意点

- setup执行的时机
  - 在beforeCreate之前执行一次，this是undefined。
  
- setup的参数
  - props：值为对象，包含：组件外部传递过来，且组件内部声明接收了的属性。
  - context：上下文对象
    - attrs: 值为对象，包含：组件外部传递过来，但没有在props配置中声明的属性, 相当于 ``this.$attrs``。
    - slots: 收到的插槽内容, 相当于 ``this.$slots``。
    - emit: 分发自定义事件的函数, 相当于 ``this.$emit``。


## 7.计算属性与监视

### 1.computed函数

- 与Vue2.x中computed配置功能一致

- 写法

  ```js
  import {computed} from 'vue'
  
  setup(){
      ...
  	//计算属性——简写
      let fullName = computed(()=>{
          return person.firstName + '-' + person.lastName
      })
      //计算属性——完整
      let fullName = computed({
          get(){
              return person.firstName + '-' + person.lastName
          },
          set(value){
              const nameArr = value.split('-')
              person.firstName = nameArr[0]
              person.lastName = nameArr[1]
          }
      })
  }
  ```

### 2.watch函数

- 与Vue2.x中watch配置功能一致

- 两个小“坑”：

  - 监视reactive定义的响应式数据时：oldValue无法正确获取、强制开启了深度监视（deep配置失效）。
  - 监视reactive定义的响应式数据中某个属性时：deep配置有效。
  
  ```js
  //情况一：监视ref定义的响应式数据
  watch(sum,(newValue,oldValue)=>{
  	console.log('sum变化了',newValue,oldValue)
  },{immediate:true})
  
  //情况二：监视多个ref定义的响应式数据
  watch([sum,msg],(newValue,oldValue)=>{
  	console.log('sum或msg变化了',newValue,oldValue)
  }) 
  
  /* 情况三：监视reactive定义的响应式数据
  			若watch监视的是reactive定义的响应式数据，则无法正确获得oldValue！！
  			若watch监视的是reactive定义的响应式数据，则强制开启了深度监视 
  */
  watch(person,(newValue,oldValue)=>{
  	console.log('person变化了',newValue,oldValue)
  },{immediate:true,deep:false}) //此处的deep配置不再奏效
  
  //情况四：监视reactive定义的响应式数据中的某个属性
  watch(()=>person.job,(newValue,oldValue)=>{
  	console.log('person的job变化了',newValue,oldValue)
  },{immediate:true,deep:true}) 
  
  //情况五：监视reactive定义的响应式数据中的某些属性
  watch([()=>person.job,()=>person.name],(newValue,oldValue)=>{
  	console.log('person的job变化了',newValue,oldValue)
  },{immediate:true,deep:true})
  
  //特殊情况
  watch(()=>person.job,(newValue,oldValue)=>{
      console.log('person的job变化了',newValue,oldValue)
  },{deep:true}) //此处由于监视的是reactive素定义的对象中的某个属性，所以deep配置有效
  ```

### 3.watchEffect函数

- watch的套路是：既要指明监视的属性，也要指明监视的回调。

- watchEffect的套路是：不用指明监视哪个属性，监视的回调中用到哪个属性，那就监视哪个属性。

- watchEffect有点像computed：

  - 但computed注重的计算出来的值（回调函数的返回值），所以必须要写返回值。
  - 而watchEffect更注重的是过程（回调函数的函数体），所以不用写返回值。

  ```js
  //watchEffect所指定的回调中用到的数据只要发生变化，则直接重新执行回调。
  watchEffect(()=>{
      const x1 = sum.value
      const x2 = person.age
      console.log('watchEffect配置的回调执行了')
  })
  ```

## 8.生命周期

<div style="display:flex;text-align:center">
<div style="border:1px solid black;width:50%"><strong>vue2.x的生命周期</strong><img src="http://blog.joych3n.com/wp-content/uploads/2022/09/lifecycle.png" alt="lifecycle_2" style="width:100%" /></div>
<div style="border:1px solid black;width:50%"><strong>vue3.0的生命周期</strong><img src="http://blog.joych3n.com/wp-content/uploads/2022/09/lifecycle.16e4c08e.png" alt="lifecycle_2" style="width:100%" /></div>
</div>

- Vue3.0中可以继续使用Vue2.x中的生命周期钩子，但有有两个被更名：
  - ``beforeDestroy``改名为 ``beforeUnmount``
  - ``destroyed``改名为 ``unmounted``
- Vue3.0也提供了 Composition API 形式的生命周期钩子，与Vue2.x中钩子对应关系如下：

|Vue2|对应|Vue3|
|---:|:--:|:---|
|`beforeCreate`|=>|`setup()`|
|`created`|=>|`setup()`|
|`beforeMount`|=>|`onBeforeMount`|
|`mounted`|=>|`onMounted`|
|`beforeUpdate`|=>|`onBeforeUpdate`|
|`updated`|=>|`onUpdated`|
|`beforeUnmount`|=>|`onBeforeUnmount`|
|`unmounted`|=>|`onUnmounted`|

## 9.自定义hook函数

- 什么是hook？—— 本质是一个函数，把setup函数中使用的Composition API进行了封装。

- 类似于vue2.x中的mixin。

- 自定义hook的优势: 复用代码, 让setup中的逻辑更清楚易懂。



## 10.toRef

- 作用：创建一个 ref 对象，其value值指向另一个对象中的某个属性。
- 语法：``const name = toRef(person,'name')``
- 应用:   要将响应式对象中的某个属性单独提供给外部使用时。


- 扩展：``toRefs`` 与``toRef``功能一致，但可以批量创建多个 ref 对象，语法：``toRefs(person)``


# 三、其它 Composition API

## 1.shallowReactive 与 shallowRef

- shallowReactive：只处理对象最外层属性的响应式（浅响应式）。
- shallowRef：只处理基本数据类型的响应式, 不进行对象的响应式处理。

- 什么时候使用?
  -  如果有一个对象数据，结构比较深, 但变化时只是外层属性变化 ===> shallowReactive。
  -  如果有一个对象数据，后续功能不会修改该对象中的属性，而是生新的对象来替换 ===> shallowRef。

## 2.readonly 与 shallowReadonly

- readonly: 让一个响应式数据变为只读的（深只读）。
- shallowReadonly：让一个响应式数据变为只读的（浅只读）。
- 应用场景: 不希望数据被修改时。

## 3.toRaw 与 markRaw

- toRaw：
  - 作用：将一个由``reactive``生成的<strong style="color:orange">响应式对象</strong>转为<strong style="color:orange">普通对象</strong>。
  - 使用场景：用于读取响应式对象对应的普通对象，对这个普通对象的所有操作，不会引起页面更新。
- markRaw：
  - 作用：标记一个对象，使其永远不会再成为响应式对象。
  - 应用场景:
    1. 有些值不应被设置为响应式的，例如复杂的第三方类库等。
    2. 当渲染具有不可变数据源的大列表时，跳过响应式转换可以提高性能。

## 4.customRef

- 作用：创建一个自定义的 ref，并对其依赖项跟踪和更新触发进行显式控制。

- 实现防抖效果：

  ```js
  <template>
  	<input type="text" v-model="keyword">
  	<h3>{{keyword}}</h3>
  </template>
  
  <script>
  	import {ref,customRef} from 'vue'
  	export default {
  		name:'Demo',
  		setup(){
  			// let keyword = ref('hello') //使用Vue准备好的内置ref
  			//自定义一个myRef
  			function myRef(value,delay){
  				let timer
  				//通过customRef去实现自定义
  				return customRef((track,trigger)=>{
  					return{
  						get(){
  							track() //告诉Vue这个value值是需要被“追踪”的
  							return value
  						},
  						set(newValue){
  							clearTimeout(timer)
  							timer = setTimeout(()=>{
  								value = newValue
  								trigger() //告诉Vue去更新界面
  							},delay)
  						}
  					}
  				})
  			}
  			let keyword = myRef('hello',500) //使用程序员自定义的ref
  			return {
  				keyword
  			}
  		}
  	}
  </script>
  ```

  

## 5.provide 与 inject

<img src="http://blog.joych3n.com/wp-content/uploads/2022/09/provide-inject.3e0505e4.png" style="width:300px" />

- 作用：实现<strong style="color:#DD5145">祖与后代组件间</strong>通信

- 套路：父组件有一个 `provide` 选项来提供数据，后代组件有一个 `inject` 选项来开始使用这些数据

- 具体写法：

  1. 祖组件中：

     ```js
     setup(){
     	......
         let car = reactive({name:'奔驰',price:'40万'})
         provide('car',car)
         ......
     }
     ```

  2. 后代组件中：

     ```js
     setup(props,context){
     	......
         const car = inject('car')
         return {car}
     	......
     }
     ```

## 6.响应式数据的判断

- isRef: 检查一个值是否为一个 `ref` 对象
- isReactive: 检查一个对象是否是由 `reactive` 创建的响应式代理
- isReadonly: 检查一个对象是否是由 `readonly` 创建的只读代理
- isProxy: 检查一个对象是否是由 `reactive` 或者 `readonly` 方法创建的代理

# 四、Composition API 的优势

## 1.Options API 存在的问题

使用传统OptionsAPI中，新增或者修改一个需求，就需要分别在data，methods，computed里修改 。

<div style="display:flex;text-align:center">
<div style="width:50%;border:1px solid #eee">
    <img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/f84e4e2c02424d9a99862ade0a2e4114~tplv-k3u1fbpfcp-watermark.image" />
</div>
<div style="width:50%;border:1px solid #eee">
    <img src="https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/e5ac7e20d1784887a826f6360768a368~tplv-k3u1fbpfcp-watermark.image" />
</div>
</div>

## 2.Composition API 的优势

我们可以更加优雅的组织我们的代码，函数。让相关功能的代码更加有序的组织在一起。
<div style="display:flex;text-align:center">
<div style="width:50%;border:1px solid #eee">
    <img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/bc0be8211fc54b6c941c036791ba4efe~tplv-k3u1fbpfcp-watermark.image"style="height:360px"/>
</div>
<div style="width:50%;border:1px solid #eee">
    <img src="https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/6cc55165c0e34069a75fe36f8712eb80~tplv-k3u1fbpfcp-watermark.image"style="height:360px"/>
</div>
</div>

# 五、新的组件

## 1.Fragment

- 在Vue2中: 组件必须有一个根标签
- 在Vue3中: 组件可以没有根标签, 内部会将多个标签包含在一个Fragment虚拟元素中
- 好处: 减少标签层级, 减小内存占用

## 2.Teleport

- 什么是Teleport？—— `Teleport` 是一种能够将我们的<strong style="color:#DD5145">组件html结构</strong>移动到指定位置的技术。

  ```js
  <teleport to="移动位置">
  	<div v-if="isShow" class="mask">
  		<div class="dialog">
  			<h3>我是一个弹窗</h3>
  			<button @click="isShow = false">关闭弹窗</button>
  		</div>
  	</div>
  </teleport>
  ```

## 3.Suspense

- 等待异步组件时渲染一些额外内容，让应用有更好的用户体验

- 使用步骤：

  - 异步引入组件

    ```js
    import {defineAsyncComponent} from 'vue'
    const Child = defineAsyncComponent(()=>import('./components/Child.vue'))
    ```

  - 使用``Suspense``包裹组件，并配置好``default`` 与 ``fallback``

    ```js
    <template>
    	<div class="app">
    		<h3>我是App组件</h3>
    		<Suspense>
    			<template v-slot:default>
    				<Child/>
    			</template>
    			<template v-slot:fallback>
    				<h3>加载中.....</h3>
    			</template>
    		</Suspense>
    	</div>
    </template>
    ```

# 六、其他

## 1.全局API的转移

- Vue 2.x 有许多全局 API 和配置。
  - 例如：注册全局组件、注册全局指令等。

    ```js
    //注册全局组件
    Vue.component('MyButton', {
      data: () => ({
        count: 0
      }),
      template: '<button @click="count++">Clicked {{ count }} times.</button>'
    })
    
    //注册全局指令
    Vue.directive('focus', {
      inserted: el => el.focus()
    }
    ```

- Vue3.0中对这些API做出了调整：

  - 将全局的API，即：``Vue.xxx``调整到应用实例（``app``）上

    | 2.x 全局 API（``Vue``） | 3.x 实例 API (`app`)                        |
    | ------------------------- | ------------------------------------------- |
    | Vue.config.xxxx           | app.config.xxxx                             |
    | Vue.config.productionTip  | <strong style="color:#DD5145">移除</strong> |
    | Vue.component             | app.component                               |
    | Vue.directive             | app.directive                               |
    | Vue.mixin                 | app.mixin                                   |
    | Vue.use                   | app.use                                     |
    | Vue.prototype             | app.config.globalProperties                 |
  

## 2.其他改变

- data选项应始终被声明为一个函数。

- 过度类名的更改：

  - Vue2.x写法

    ```css
    .v-enter,
    .v-leave-to {
      opacity: 0;
    }
    .v-leave,
    .v-enter-to {
      opacity: 1;
    }
    ```

  - Vue3.x写法

    ```css
    .v-enter-from,
    .v-leave-to {
      opacity: 0;
    }
    
    .v-leave-from,
    .v-enter-to {
      opacity: 1;
    }
    ```

- <strong style="color:#DD5145">移除</strong>keyCode作为 v-on 的修饰符，同时也不再支持``config.keyCodes``

- <strong style="color:#DD5145">移除</strong>``v-on.native``修饰符

  - 父组件中绑定事件

    ```js
    <my-component
      v-on:close="handleComponentEvent"
      v-on:click="handleNativeClickEvent"
    />
    ```

  - 子组件中声明自定义事件

    ```js
    <script>
      export default {
        emits: ['close']
      }
    </script>
    ```

- <strong style="color:#DD5145">移除</strong>过滤器（filter）

  > 过滤器虽然这看起来很方便，但它需要一个自定义语法，打破大括号内表达式是 “只是 JavaScript” 的假设，这不仅有学习成本，而且有实现成本！建议用方法调用或计算属性去替换过滤器。

- ......