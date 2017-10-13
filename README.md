# Vue2DevNote
项目说明：学习Vue2全家桶：`vue2.js`、`vue-cli`、`vue-router`、`vuex` 的笔记。

- [**Vue2.0官方网站**](http://vuejs.org/)
- [**Vue相关开源项目库汇总(史上最全)**](http://blog.csdn.net/caijunfen/article/details/78221680)


## 目录结构

- [vue2.js](#1.0.0)
    - [内部指令](#1.1.0)
        - [走起我的vue2.0](#1.1.1)
        - [v-if  v-else  v-show 指令](#1.1.2)
        - [v-for指令：解决模板循环问题](#1.1.3)
        - [v-text & v-html](#1.1.4)
        - [v-on：绑定事件监听器](#1.1.5)
        - [v-model指令](#1.1.6)
        - [v-bind 指令](#1.1.7)
        - [其他内部指令(v-pre & v-cloak & v-once)](#1.1.8)
    - [全局API](#1.2.0)
        - [Vue.directive 自定义指令](#1.2.1)
        - [Vue.extend构造器的延伸](#1.2.2)
        - [Vue.set全局操作](#1.2.3)
        - [Vue的生命周期（钩子函数）](#1.2.4)
        - [Template 制作模版](#1.2.5)
        - [Component 初识组件](#1.2.6)
        - [Component 组件 props 属性设置](#1.2.7)
        - [Component 父子组件关系](#1.2.8)
        - [Component 标签](#1.2.9)
    - [选项](#1.3.0)
        - [propsData Option  全局扩展的数据传递](#1.3.1)
        - [computed Option  计算选项](#1.3.2)
        - [Methods Option  方法选项](#1.3.3)
        - [Watch 选项 监控数据](#1.3.4)
        - [Mixins 混入选项操作](#1.3.5)
        - [Extends Option  扩展选项](#1.3.6)
    - [实例和内置组件](#1.4.0)
        - [实例入门-实例属性](#1.4.1)
        - [实例方法](#1.4.2)
        - [实例事件](#1.4.3)
        - [内置组件 -slot讲解](#1.4.4)
- [vue-cli](#2.0.0)
    - [Vue-cli 开始吧骚年](#2.1.0)
    - [Vue-cli 项目结构讲解](#2.2.0)
    - [解读Vue-cli的模板](#2.3.0)
- [vue-router](#3.0.0)
    - [vue-router入门](#3.1.0)
    - [vue-router配置子路由](#3.2.0)
    - [vue-router如何参数传递](#3.3.0)
    - [单页面多路由区域操作](#3.4.0)
    - [vue-router 利用url传递参数](#3.5.0)
    - [vue-router 的重定向-redirect](#3.6.0)
    - [alias别名的使用](#3.7.0)
    - [路由的过渡动画](#3.8.0)
    - [mode的设置和404页面的处理](#3.9.0)
    - [路由中的钩子](#3.10.0)
    - [编程式导航](#3.11.0)
- [vuex](#4.0.0)
    - [初出茅庐 来个小Demo](#4.1.0)
    - [state访问状态对象](#4.2.0)
    - [mutations修改状态](#4.3.0)
    - [getters计算过滤操作](#4.4.0)
    - [actions异步修改状态](#4.5.0)
    - [module模块组](#4.6.0)
- [参考资料](#5.0.0)


<h2 id="1.0.0"> 1、vue2.js</h2>

<h3 id="1.1.0"> 1.1、内部指令</h3>

- <h5 id="1.1.1"> 1.1.1、走起我的vue2.0</h5>

    [**Vue 官方网站**](http://vuejs.org/)
    [**Vue Github**](https://github.com/vuejs/vue)

    **开发版本**：包含完整的警告和调试模式 
    **生产版本**：删除了警告，进行了压缩 

- <h5 id="1.1.2"> 1.1.2、v-if  v-else  v-show 指令</h5>

    **v-if**： 判断是否加载html的DOM，可以减轻服务器的压力，在需要时加载。 
    **v-show**：调整css中display属性，DOM已经加载，只是CSS控制没有显示出来，可以使客户端操作更加流畅。

- <h5 id="1.1.3"> 1.1.3、v-for指令 ：解决模板循环问题</h5>

    `v-for指令`是循环渲染一组data中的数组，v-for 指令需要以 item in items 形式的特殊语法，items 是源数据数组并且item是数组元素迭代的别名。[ 还可以添加index序号，形如：（item,index） in items ]。

    **排序：在computed中进行调用排序。**
    ```
    // 数组对象方法排序:
    function sortByKey(array, key) {
        return array.sort(function(a, b) {
            var x = a[key];
            var y = b[key];
            return ((x < y) ? -1 : ((x > y) ? 1 : 0));
        });
    }
    ```

- <h5 id="1.1.4"> 1.1.4、v-text & v-html</h5>

    1. 输出data中的值用的是 {{xxx}}，这种情况是有弊端的，就是当网速很慢或javascript出错时，会暴露 {{xxx}}。Vue提供v-text，就是解决这个问题。
    2. 双大括号会将数据解释为纯文本，而非HTML。为了输出真正的HTML，需要使用v-html 指令。
    3. 需要注意：在生产环境中动态渲染HTML是非常危险的，因为容易导致XSS攻击。所以只能在可信的内容上使用v-html，永远不要在用户提交和可操作的网页上使用。

- <h5 id="1.1.5"> 1.1.5、v-on：绑定事件监听器</h5>

    `v-on` 就是监听事件，可以用`v-on`指令监听DOM事件来触发一些javascript代码。[ **v-on:click 等价于 @click** ]

    除了绑定click之外，我们还可以绑定其它事件，比如键盘回车事件v-on:keyup.enter事件。

- <h5 id="1.1.6"> 1.1.6、v-model指令</h5>

    v-model指令，可理解为绑定数据源。就是把数据绑定在特定的表单元素上，可以很容易的实现双向数据绑定。

    **修饰符**
    1. **.lazy**：取代 imput 监听 change 事件(input失去焦点时生效)。
    2. **.number**：输入字符串转为数字(第一个输入数字有效，若是字母则无效)。
    3. **.trim**：输入去掉首尾空格。

- <h5 id="1.1.7"> 1.1.7、v-bind 指令</h5>

    v-bind是处理HTML中的标签属性的，例如div就是一个标签，img也是一个标签，我们绑定img上的src进行动态赋值。[ 在绑定CSS样式时，绑定的值必须在vue中的data属性中进行声明。**v-bind:xxx 等价于 :xxx** ]

- <h5 id="1.1.8"> 1.1.8、其他内部指令(v-pre & v-cloak & v-once)</h5>

    1. **v-pre指令**：在模板中跳过vue的编译，直接输出原始值。就是在标签中加入v-pre就不会输出vue中的data值了。
    2. **v-cloak指令**：在vue渲染完指定的整个DOM后才进行显示。它必须和CSS样式一起使用。
    3. ** v-once指令**：在第一次DOM时进行渲染，渲染完成后视为静态内容，跳出以后的渲染过程。

---


<h3 id="1.2.0"> 1.2、全局API</h3>

    全局API并不在构造器里，而是先声明全局变量或者直接在Vue上定义一些新功能，Vue内置了一些全局API，比如Vue.directive。说的简单些就是，在构造器外部用Vue提供给我们的API函数来定义新的功能。

- <h5 id="1.2.1"> 1.2.1、Vue.directive 自定义指令</h5>

    1. **自定义指令中传递的三个参数**
    - **el**： 指令所绑定的元素，可以用来直接操作DOM。
    - **binding**： 一个对象，包含指令的很多信息。
    - **vnode**：Vue编译生成的虚拟节点。

    2. **自定义指令的生命周期**

    自定义指令有五个生命周期（也叫 `钩子函数`），分别是 bind，inserted，update，componentUpdated，unbind。

    - **bind**：只调用一次，指令第一次绑定到元素时调用，用这个钩子函数可以定义一个绑定时执行一次的初始化动作。
    - **inserted**：被绑定元素插入父节点时调用（父节点存在即可调用，不必存在于document中）。
    - **update**：被绑定于元素所在的模板更新时调用，而无论绑定值是否变化。通过比较更新前后的绑定值，可以忽略不必要的模板更新。
    - **componentUpdated**：被绑定元素所在模板完成一次更新周期时调用。
    - **unbind**：只调用一次，指令与元素解绑时调用。

- <h5 id="1.2.2"> 1.2.2、Vue.extend 构造器的延伸</h5>

    1. Vue.extend 返回的是一个“扩展实例构造器”，也就是预设了部分选项的Vue实例构造器。经常服务于Vue.component用来生成组件，可以简单理解为当在模板中遇到该组件名称作为标签的自定义元素时，会自动调用“扩展实例构造器”来生产组件实例，并挂载到自定义元素上。
    2. 挂载到普通标签上 ---- 还可以通过HTML标签上的id或者class来生成扩展实例构造器，Vue.extend里的代码是一样的，只是在挂载的时候，我们用类似jquery的选择器的方法，来进行挂载就可以了。

- <h5 id="1.2.3"> 1.2.3、Vue.set 全局操作</h5>

- <h5 id="1.2.4"> 1.2.4、Vue的生命周期（钩子函数）</h5>

- <h5 id="1.2.5"> 1.2.5、Template 制作模版</h5>

- <h5 id="1.2.6"> 1.2.6、Component 初识组件</h5>

- <h5 id="1.2.7"> 1.2.7、Component 组件props 属性设置</h5>

- <h5 id="1.2.8"> 1.2.8、Component 父子组件关系</h5>

- <h5 id="1.2.9"> 1.2.9、Component 标签</h5>
 
---


<h3 id="1.3.0"> 1.3、选项</h3>

- <h5 id="1.3.1"> 1.3.1、propsData Option  全局扩展的数据传递</h5>

- <h5 id="1.3.2"> 1.3.2、computed Option  计算选项</h5>

- <h5 id="1.3.3"> 1.3.3、Methods Option  方法选项</h5>

- <h5 id="1.3.4"> 1.3.4、Watch 选项 监控数据</h5>

- <h5 id="1.3.5"> 1.3.5、Mixins 混入选项操作</h5>

- <h5 id="1.3.6"> 1.3.6、Extends Option  扩展选项</h5>


---


<h3 id="1.4.0"> 1.4、选项</h3>

- <h5 id="1.4.1"> 1.4.1、实例入门-实例属性</h5>

- <h5 id="1.4.2"> 1.4.2、实例方法</h5>

- <h5 id="1.4.3"> 1.4.3、实例事件</h5>

- <h5 id="1.4.4"> 1.4.4、内置组件 -slot讲解</h5>


---


<h2 id="2.0.0"> 2、vue-cli</h2>

<h3 id="2.1.0"> 2.1、Vue-cli 开始吧骚年</h3>

<h3 id="2.2.0"> 2.2、Vue-cli 项目结构讲解</h3>

<h3 id="2.3.0"> 2.3、解读Vue-cli的模板</h3>


---


<h2 id="3.0.0"> 3、vue-router</h2>

<h3 id="3.1.0"> 3.1、vue-router入门</h3>

<h3 id="3.2.0"> 3.2、vue-router配置子路由</h3>

<h3 id="3.3.0"> 3.3、vue-router如何参数传递</h3>

<h3 id="3.4.0"> 3.4、单页面多路由区域操作</h3>

<h3 id="3.5.0"> 3.5、vue-router 利用url传递参数</h3>

<h3 id="3.6.0"> 3.6、vue-router 的重定向-redirect</h3>

<h3 id="3.7.0"> 3.7、alias别名的使用</h3>

<h3 id="3.8.0"> 3.8、路由的过渡动画</h3>

<h3 id="3.9.0"> 3.9、mode的设置和404页面的处理</h3>

<h3 id="3.10.0"> 3.10、路由中的钩子</h3>

<h3 id="3.11.0"> 3.11、编程式导航.</h3>


---


<h2 id="4.0.0"> 4、vuex</h2>

<h3 id="4.1.0"> 4.1、初出茅庐 来个小Demo</h3>

<h3 id="4.2.0"> 4.2、state访问状态对象</h3>

<h3 id="4.3.0"> 4.3、Mutations修改状态</h3>

<h3 id="4.4.0"> 4.4、getters计算过滤操作</h3>

<h3 id="4.5.0"> 4.5、actions异步修改状态</h3>

<h3 id="4.6.0"> 4.6、module模块组</h3>

---


<h2 id="5.0.0"> 5、参考资料</h2>


---


# License

```
 Copyright (c) 2017, The Jeterlee authors 

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.
```
