# Vue2DevNote
项目说明：学习Vue2全家桶：`vue2.js`、`vue-cli`、`vue-router`、`vuex` 的笔记。

[**Vue2.0官方网站**](http://vuejs.org/)


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

- <h3 id="1.1.0"> 1.1、内部指令</h3>

    - <h3 id="1.1.1"> 1.1.1、走起我的vue2.0</h3>

    [**Vue官方网站**](http://vuejs.org/)
    
    **开发版本**：包含完整的警告和调试模式 
    **生产版本**：删除了警告，进行了压缩 

    - <h3 id="1.1.2"> 1.1.2、v-if  v-else  v-show 指令</h3>

    **v-if**： 判断是否加载html的DOM，可以减轻服务器的压力，在需要时加载。 
    **v-show**：调整css中display属性，DOM已经加载，只是CSS控制没有显示出来，可以使客户端操作更加流畅。
    
    - <h3 id="1.1.3"> 1.1.3、v-for指令 ：解决模板循环问题</h3>
    
    - <h3 id="1.1.4"> 1.1.4、v-text & v-html</h3>
    
    - <h3 id="1.1.5"> 1.1.5、v-on：绑定事件监听器</h3>
    
    - <h3 id="1.1.6"> 1.1.6、v-model指令</h3>
    
    - <h3 id="1.1.7"> 1.1.7、v-bind 指令</h3>
    
    - <h3 id="1.1.8"> 1.1.8、其他内部指令(v-pre & v-cloak & v-once)</h3>

---


- <h3 id="1.2.0"> 1.2、全局API</h3>
    
    - <h3 id="1.2.1"> 1.2.1、Vue.directive 自定义指令</h3>
    
    - <h3 id="1.2.2"> 1.2.2、Vue.extend 构造器的延伸</h3>
    
    - <h3 id="1.2.3"> 1.2.3、Vue.set 全局操作</h3>
    
    - <h3 id="1.2.4"> 1.2.4、Vue的生命周期（钩子函数）</h3>
    
    - <h3 id="1.2.5"> 1.2.5、Template 制作模版</h3>
    
    - <h3 id="1.2.6"> 1.2.6、Component 初识组件</h3>
    
    - <h3 id="1.2.7"> 1.2.7、Component 组件props 属性设置</h3>
    
    - <h3 id="1.2.8"> 1.2.8、Component 父子组件关系</h3>

    - <h3 id="1.2.9"> 1.2.9、Component 标签</h3>
 
---


- <h3 id="1.3.0"> 1.3、选项</h3>

    - <h3 id="1.3.1"> 1.3.1、propsData Option  全局扩展的数据传递</h3>

    - <h3 id="1.3.2"> 1.3.2、computed Option  计算选项</h3>

    - <h3 id="1.3.3"> 1.3.3、Methods Option  方法选项</h3>

    - <h3 id="1.3.4"> 1.3.4、Watch 选项 监控数据</h3>

    - <h3 id="1.3.5"> 1.3.5、Mixins 混入选项操作</h3>

    - <h3 id="1.3.6"> 1.3.6、Extends Option  扩展选项</h3>


---


- <h3 id="1.4.0"> 1.4、选项</h3>

    - <h3 id="1.4.1"> 1.4.1、实例入门-实例属性</h3>

    - <h3 id="1.4.2"> 1.4.2、实例方法</h3>

    - <h3 id="1.4.3"> 1.4.3、实例事件</h3>

    - <h3 id="1.4.4"> 1.4.4、内置组件 -slot讲解</h3>


---


<h2 id="2.0.0"> 2、vue-cli</h2>

- <h3 id="2.1.0"> 2.1、Vue-cli 开始吧骚年</h3>

- <h3 id="2.2.0"> 2.2、Vue-cli 项目结构讲解</h3>

- <h3 id="2.3.0"> 2.3、解读Vue-cli的模板</h3>


---


<h2 id="3.0.0"> 3、vue-router</h2>

- <h3 id="3.1.0"> 3.1、vue-router入门</h3>

- <h3 id="3.2.0"> 3.2、vue-router配置子路由</h3>

- <h3 id="3.3.0"> 3.3、vue-router如何参数传递</h3>

- <h3 id="3.4.0"> 3.4、单页面多路由区域操作</h3>

- <h3 id="3.5.0"> 3.5、vue-router 利用url传递参数</h3>

- <h3 id="3.6.0"> 3.6、vue-router 的重定向-redirect</h3>

- <h3 id="3.7.0"> 3.7、alias别名的使用</h3>

- <h3 id="3.8.0"> 3.8、路由的过渡动画</h3>

- <h3 id="3.9.0"> 3.9、mode的设置和404页面的处理</h3>

- <h3 id="3.10.0"> 3.10、路由中的钩子</h3>

- <h3 id="3.11.0"> 3.11、编程式导航.</h3>


---


<h2 id="4.0.0"> 4、vuex</h2>

- <h3 id="4.1.0"> 4.1、初出茅庐 来个小Demo</h3>

- <h3 id="4.2.0"> 4.2、state访问状态对象</h3>

- <h3 id="4.3.0"> 4.3、Mutations修改状态</h3>

- <h3 id="4.4.0"> 4.4、getters计算过滤操作</h3>

- <h3 id="4.5.0"> 4.5、actions异步修改状态</h3>

- <h3 id="4.6.0"> 4.6、module模块组</h3>

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
