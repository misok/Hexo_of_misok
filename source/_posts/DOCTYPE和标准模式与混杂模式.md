title: DOCTYPE与标准模式与混杂模式
date: 2015-3-18
categories: 前端开发
tags: [HTML, CSS]

---

```
写作目的：
介绍下什么是标准模式与混杂模式
怎么开启它们
与DOCTYPE的关系
怎么检测
```
<!-- more -->
###DOCTYPE是什么
DOCTYPE：文档类型声明，它告诉浏览器以哪种标准来解析文档。
DOCTYPE定义了三种DTD（文档类型定义）：
- 严格版本
- 过渡版本
- 基于框架的HTML
```
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01//EN"
"http://www.w3.org//TR/html4/strict.dtd">     HTML4.01
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN"
"http://www.w3.org//TR/xhtml11/DTD//xhtml11.dtd">  XHTML1.1
<!DOCTYPE html> HTML5
```
以上三个是几个常见的DOCTYPE写法。

###标准模式与混杂模式
而所谓标准模式和混杂模式，是浏览器厂商为了保证浏览器的向后兼容性而创建的两种呈现模式。而这两种模式的触发与DOCTYPE是否存在以及使用哪种DTD有关。

- 如果XHTML包含完整的DOCTYPE，则它一般以标准模式呈现
- 对于HTML4.01文档
  - DTD若为严格版本，则页面一般以标准模式呈现
  - DTD若为过渡版本且带有URL，则页面以标准模式呈现；如果DTD为过度版本但是没有URL，则页面以混杂模式呈现
- DOCTYPE不存在或者形式不正确，页面以混杂模式呈现
- HTML5页面以标准模式呈现

###如何检测
可以通过document.compatMODE来检测文档以哪种模式渲染的。
- 若document.compatMODE值为css1Compat,则为标准模式
- 若document.compatMODE值为BackCompat则为混杂模式
- 若document.compatMODE值为undefined则为混杂模式

注：使用标准模式与混杂模式会有许多细微区别，不同浏览器不同标准表现都不一样，但是使用标准模式对页面的要求更为严格。
