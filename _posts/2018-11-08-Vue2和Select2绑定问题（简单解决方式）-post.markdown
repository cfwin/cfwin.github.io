---
layout: post
title: Vue2和Select2绑定问题（简单解决方式）
date: 2018-11-08 11:32:24.000000000 +09:00
catalog: 	 true
categories: Javascript
tags:
    - Vue
    - Select2
---


工作上碰到Vue和Select2结合问题,简单点，问题解决。

~~~
Vue.directive('select2', {
    twoWay: true,
    bind: function (el, binding, vnode) {
    	$(el).select2().on("select2:select", (e) => {
 			el.dispatchEvent(new Event('change', { target: e.target }));
		});
    }
});
var app = new Vue({
  el: '#app',
});
~~~

~~~
<select
      class="form-control select2-control"
      multiple="" 
      tabindex="-1"
      v-select2="category" <--主要
      v-model="category" <--主要
>
      <option :value="item_key" v-for="(item_value, item_key) in categories">{{ item_value }}</option>
</select>
~~~
