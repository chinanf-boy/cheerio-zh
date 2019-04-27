# cheeriojs/cheerio [![explain]][source] [![translate-svg]][translate-list]

<!-- [![size-img]][size] -->

[explain]: http://llever.com/explain.svg
[source]: https://github.com/chinanf-boy/Source-Explain
[translate-svg]: http://llever.com/translate.svg
[translate-list]: https://github.com/chinanf-boy/chinese-translate-list
[size-img]: https://packagephobia.now.sh/badge?p=Name
[size]: https://packagephobia.now.sh/result?p=Name

「 快, 灵活 & 轻 的 jQuery 核心实现，特别为服务器端(Node)设计。 」

[中文](./readme.md) | [english](https://github.com/cheeriojs/cheerio)

---

## 校对 🀄️

<!-- doc-templite START generated -->
<!-- repo = 'cheeriojs/cheerio' -->
<!-- commit = '7a9ff22f68bd6dbdf04f8e3a52e28a6b369b5fa7' -->
<!-- time = '2019-04-22' -->

| 翻译的原文 | 与日期        | 最新更新 | 更多                       |
| ---------- | ------------- | -------- | -------------------------- |
| [commit]   | ⏰ 2019-04-22 | ![last]  | [中文翻译][translate-list] |

[last]: https://img.shields.io/github/last-commit/cheeriojs/cheerio.svg
[commit]: https://github.com/cheeriojs/cheerio/tree/7a9ff22f68bd6dbdf04f8e3a52e28a6b369b5fa7

<!-- doc-templite END generated -->

### 贡献

欢迎 👏 勘误/校对/更新贡献 😊 [具体贡献请看](https://github.com/chinanf-boy/chinese-translate-list#贡献)

## 生活

[help me live , live need money 💰](https://github.com/chinanf-boy/live-need-money)

---

<h1 align="center">cheerio</h1>

<h5 align="center">快, 灵活 & 轻 的jQuery 核心实现，特别为服务器端设计。</h5>

<div align="center">
  <a href="http://travis-ci.org/cheeriojs/cheerio">
    <img src="https://secure.travis-ci.org/cheeriojs/cheerio.svg?branch=master" alt="Travis CI" />
  </a>
  <a href="https://coveralls.io/r/cheeriojs/cheerio">
    <img src="http://img.shields.io/coveralls/cheeriojs/cheerio.svg?branch=master&style=flat" alt="Coverage" />
  </a>
  <a href="https://gitter.im/cheeriojs/cheerio?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge">
    <img src="https://badges.gitter.im/Join%20Chat.svg" alt="Join the chat at https://gitter.im/cheeriojs/cheerio" />
  </a>
  <a href="#backers">
    <img src="https://opencollective.com/cheerio/backers/badge.svg" alt="OpenCollective backers"/>
  </a>
  <a href="#sponsors">
    <img src="https://opencollective.com/cheerio/sponsors/badge.svg" alt="OpenCollective sponsors"/>
  </a>
</div>

<br />

```js
const cheerio = require('cheerio');
const $ = cheerio.load('<h2 class="title">Hello world</h2>');

$('h2.title').text('Hello there!');
$('h2').addClass('welcome');

$.html();
//=> <h2 class="title welcome">Hello there!</h2>
```

## 注意

我们目前正在 `master`分支，致力 cheerio 1.0.0 版本的发布。上次源代码发布的版本是，`0.22.0`， 可以在[这里](https://github.com/cheeriojs/cheerio/tree/aa90399c9c02f12432bfff97b8f1c7d8ece7c307)找到。

## 安装

`npm install cheerio`

## 特征

**❤ 熟悉的语法：** Cheerio 实现了 jQuery 核心 的一个子集。Cheerio 从 jQuery 库中，删除了所有 DOM 和浏览器不一致的残骸，揭示了它真正华丽的 API。

**ϟ 非常快：**Cheerio 使用非常简单，一致的 DOM 模型。因此，解析，操纵和渲染非常有效。初步的端到端基准测试表明，cheerio 是**8x**快于 JSDOM 。

**❁ 非常灵活：**Cheerio 围绕 @FB55 宽松的[htmlparser2](https://github.com/fb55/htmlparser2/)解析器展开。Cheerio 几乎可以解析，任何 HTML 或 XML 文档。

## Cheerio 不是网络浏览器

Cheerio 解析(html)标记，并提供用于遍历/操纵，结果数据结构的 API。它不会像 Web 浏览器那样解释结果。具体来说，并*不会*生成可视化渲染，应用 CSS，加载外部资源或执行 JavaScript。如果您的用例，需要任何此功能，您应该考虑像其他项目：[PhantomJS](http://phantomjs.org/)要么[JSDom](https://github.com/tmpvar/jsdom)。

## API

### 目录

<details>
  <summary>Selectors （选择器）</summary>

- [\$( selector, \[context\], \[root\] )](#-selector-context-root-)

  </details>
  <details>
    <summary>属性</summary>

- [.attr( name, value )](#attr-name-value-)
- [.prop( name, value )](#prop-name-value-)
- [.data( name, value )](#data-name-value-)
- [.val( \[value\] )](#val-value-)
- [.removeAttr( name )](#removeattr-name-)
- [.hasClass( className )](#hasclass-classname-)
- [.addClass( className )](#addclass-classname-)
- [.removeClass( \[className\] )](#removeclass-classname-)
- [.toggleClass( className, \[switch\] )](#toggleclass-classname-switch-)
- [.is( selector )](#is-selector-)
- [.is( element )](#is-element-)
- [.is( selection )](#is-selection-)
- [.is( function(index) )](#is-functionindex-)

  </details>
  <details>
    <summary>表单</summary>

- [.serialize()](#serialize)
- [.serializeArray()](#serializearray)

  </details>
  <details>
    <summary>遍历</summary>

- [.find(selector)](#findselector)
- [.find(selection)](#findselection)
- [.find(node)](#findnode)
- [.parent(\[selector\])](#parentselector)
- [.parents(\[selector\])](#parentsselector)
- [.parentsUntil(\[selector\]\[,filter\])](#parentsuntilselectorfilter)
- [.closest(selector)](#closestselector)
- [.next(\[selector\])](#nextselector)
- [.nextAll(\[selector\])](#nextallselector)
- [.nextUntil(\[selector\], \[filter\])](#nextuntilselector-filter)
- [.prev(\[selector\])](#prevselector)
- [.prevAll(\[selector\])](#prevallselector)
- [.prevUntil(\[selector\], \[filter\])](#prevuntilselector-filter)
- [.slice( start, \[end\] )](#slice-start-end-)
- [.siblings(\[selector\])](#siblingsselector)
- [.children(\[selector\])](#childrenselector)
- [.contents()](#contents)
- [.each( function(index, element) )](#each-functionindex-element-)
- [.map( function(index, element) )](#map-functionindex-element-)
- [.filter( selector )<br>
  .filter( selection )<br>
  .filter( element )<br>
  .filter( function(index, element) )](#filter-selector---filter-selection---filter-element---filter-functionindex-element-)
- [.not( selector )<br>
  .not( selection )<br>
  .not( element )<br>
  .not( function(index, elem) )](#not-selector---not-selection---not-element---not-functionindex-elem-)
- [.has( selector )<br>
  .has( element )](#has-selector---has-element-)
- [.first()](#first)
- [.last()](#last)
- [.eq( i )](#eq-i-)
- [.get( \[i\] )](#get-i-)
- [.index()](#index)
- [.index( selector )](#index-selector-)
- [.index( nodeOrSelection )](#index-nodeorselection-)
- [.end()](#end)
- [.add( selector \[, context\] )](#add-selector--context-)
- [.add( element )](#add-element-)
- [.add( elements )](#add-elements-)
- [.add( html )](#add-html-)
- [.add( selection )](#add-selection-)
- [.addBack( \[filter\] )](#addback-filter-)

  </details>
  <details>
    <summary>操纵</summary>

- [.append( content, \[content, ...\] )](#append-content-content--)
- [.appendTo( target )](#appendto-target-)
- [.prepend( content, \[content, ...\] )](#prepend-content-content--)
- [.prependTo( target )](#prependto-target-)
- [.after( content, \[content, ...\] )](#after-content-content--)
- [.insertAfter( target )](#insertafter-target-)
- [.before( content, \[content, ...\] )](#before-content-content--)
- [.insertBefore( target )](#insertbefore-target-)
- [.remove( \[selector\] )](#remove-selector-)
- [.replaceWith( content )](#replacewith-content-)
- [.empty()](#empty)
- [.html( \[htmlString\] )](#html-htmlstring-)
- [.text( \[textString\] )](#text-textstring-)
- [.wrap( content )](#wrap-content-)
- [.css( \[propertName\] )<br>
  .css( \[ propertyNames\] )<br>
  .css( \[propertyName\], \[value\] )<br>
  .css( \[propertName\], \[function\] )<br>
  .css( \[properties\] )](#css-propertname---css--propertynames---css-propertyname-value---css-propertname-function---css-properties-)

</details>

### 我们将使用的标记示例：

```html
<ul id="fruits">
  <li class="apple">Apple</li>
  <li class="orange">Orange</li>
  <li class="pear">Pear</li>
</ul>
```

这里的 HTML 标记，是我们所有 API 示例的。

### 载入中

首先，您需要加载 HTML。jQuery 中的这一步是隐含的，因为 jQuery 在一个烤着的 DOM 上运行的。而 Cheerio，我们是需要传递 HTML 文档给它。

这是*首选*方法：

```js
const cheerio = require('cheerio');
const $ = cheerio.load('<ul id="fruits">...</ul>');
```

或者，您也可以通过，将字符串作为上下文传递，来加载 HTML：

```js
const $ = require('cheerio');
$('ul', '<ul id="fruits">...</ul>');
```

或者直接选择`li`元素：

```js
const $ = require('cheerio');
$('li', 'ul', '<ul id="fruits">...</ul>');
```

`.load()`还可以传递一个额外的对象，如果您需要修改任何默认解析选项的话：

```js
const $ = cheerio.load('<ul id="fruits">...</ul>', {
  normalizeWhitespace: true,
  xmlMode: true
});
```

这些解析选项，直接来自[htmlparser2](https://github.com/fb55/htmlparser2/wiki/Parser-options)，因此，任何`htmlparser2`可用的选项，在 cheerio 中也有效。默认选项是：

```js
{
    withDomLvl1: true,
    normalizeWhitespace: false,
    xmlMode: false,
    decodeEntities: true
}
```

有关选项及其效果的完整列表，请参阅[这里](https://github.com/fb55/DomHandler)和[htmlparser2 的选项](https://github.com/fb55/htmlparser2/wiki/Parser-options)。

### 选择器

Cheerio 的选择器实现，几乎与 jQuery 相同，因此 API 非常相似。

#### \$( selector, [context], [root] )

`selector`，会搜索`context`范围，而该范围又是从`root`范围搜索而来。`selector`和`context`可以是字符串表达式，DOM 元素，DOM 元素数组或 cheerio 对象。`root`通常是 HTML 文档字符串。

此选择器方法是遍历和操纵文档的起点。像 jQuery 一样，它是在文档中，选择元素的主要方法，但与 jQuery 不同，我们是构建在 CSSSelect 库之上的，实现了大多数的 Sizzle 选择器。

```js
$('.apple', '#fruits').text();
//=> Apple

$('ul .pear').attr('class');
//=> pear

$('li[class=orange]').html();
//=> Orange
```

##### XML Namespaces

您可以选择 XML 命名空间，但是[其实遵循 CSS 规范](https://www.w3.org/TR/2011/REC-css3-selectors-20110929/#attribute-selectors)，冒号（`:`）需要进行转义，才能使选择器有效。

```js
$('[xml\\:id="main"');
```

### 属性

获取和修改属性的方法。

#### .attr( name, value )

获取和设置属性的方法。仅获取匹配集里面，第一个元素的属性值。如果将属性的值设置为`null`，就删除该属性。你也可以传递一个`map`和`function`，就像 jQuery。

```js
$('ul').attr('id');
//=> fruits

$('.apple')
  .attr('id', 'favorite')
  .html();
//=> <li class="apple" id="favorite">Apple</li>
```

> 看到<http://api.jquery.com/attr/>，获得更多信息

#### .prop( name, value )

获取和设置属性的方法。仅获取匹配集里面，第一个元素的属性值。

```js
$('input[type="checkbox"]').prop('checked');
//=> false

$('input[type="checkbox"]')
  .prop('checked', true)
  .val();
//=> ok
```

> 看到<http://api.jquery.com/prop/>，获得更多信息

#### .data( name, value )

获取和设置数据属性的方法。仅获取或设置匹配集里面，第一个元素的数据属性值。

```js
$('<div data-apple-color="red"></div>').data();
//=> { appleColor: 'red' }

$('<div data-apple-color="red"></div>').data('apple-color');
//=> 'red'

const apple = $('.apple').data('kind', 'mac');
apple.data('kind');
//=> 'mac'
```

> 看到<http://api.jquery.com/data/>，获得更多信息

#### .val( [value] )

获取和设置 input，select 和 textarea 的值的方法。注意：`map`，和`function`支持尚未添加。

```js
$('input[type="text"]').val();
//=> input_text

$('input[type="text"]')
  .val('test')
  .html();
//=> <input type="text" value="test"/>
```

#### .removeAttr( name )

删除`name`属性的方法。

```js
$('.pear')
  .removeAttr('class')
  .html();
//=> <li>Pear</li>
```

#### .hasClass( className )

检查是否，匹配的 _任何_ 元素，具有给定的`className`。

```js
$('.pear').hasClass('pear');
//=> true

$('apple').hasClass('fruit');
//=> false

$('li').hasClass('pear');
//=> true
```

#### .addClass( className )

将类添加到所有匹配的元素。也接受一个`function`，就像 jQuery。

```js
$('.pear')
  .addClass('fruit')
  .html();
//=> <li class="pear fruit">Pear</li>

$('.apple')
  .addClass('fruit red')
  .html();
//=> <li class="apple fruit red">Apple</li>
```

> 看到<http://api.jquery.com/addClass/>，获得更多信息。

#### .removeClass( [className] )

从所选元素中，删除一个或多个以空格分隔的类。如果没有指定的`className`，则删除所有类。也接受一个`function`，就像 jQuery。

```js
$('.pear')
  .removeClass('pear')
  .html();
//=> <li class="">Pear</li>

$('.apple')
  .addClass('red')
  .removeClass()
  .html();
//=> <li class="">Apple</li>
```

> 看到<http://api.jquery.com/removeClass/>，获得更多信息。

#### .toggleClass( className, [switch] )

根据类的存在与否，或 switch 参数的值，从匹配的元素中，添加或删除类。也接受一个`function`，就像 jQuery。

```js
$('.apple.green')
  .toggleClass('fruit green red')
  .html();
//=> <li class="apple fruit red">Apple</li>

$('.apple.green')
  .toggleClass('fruit green red', true)
  .html();
//=> <li class="apple green fruit red">Apple</li>
```

> 看到<http://api.jquery.com/toggleClass/>，获得更多信息。

#### .is( selector )

#### .is( element )

#### .is( selection )

#### .is( function(index) )

检查当前的元素列表，如果*任何*元素与 selector 匹配，则返回`true`，。若是 element 或 Cheerio selection，那么*任何*元素匹配则返回`true`。如果使用的是一个 function，则在所选元素的上下文中，执行该函数，而`this`指当前元素。

### 表单

#### .serialize()

将一组表单元素，编码为 URL 查询字符串。

```js
$(
  '<form><input name="foo" value="bar" checked /><input name="foo" value="qux" checked /></form>'
).serialize();
//=> foo=bar&foo=qux
```

#### .serializeArray()

将一组表单元素，编码为名称和值的数组。

```js
$('<form><input name="foo" value="bar" /></form>').serializeArray();
//=> [ { name: 'foo', value: 'bar' } ]
```

### 遍历

#### .find(selector)

#### .find(selection)

#### .find(node)

获取当前匹配元素集里面，每个元素的后代。由 selector，jQuery 对象或 element 过滤。

```js
$('#fruits').find('li').length;
//=> 3
$('#fruits').find($('.apple')).length;
//=> 1
```

#### .parent([selector])

获取当前匹配元素集里面，每个元素的父元素，可选项为，通过选择器进行过滤。

```js
$('.pear')
  .parent()
  .attr('id');
//=> fruits
```

#### .parents([selector])

获取当前匹配元素集里面，由`selector`过滤而来的父辈集合

```js
$('.orange').parents().length;
// => 2
$('.orange').parents('#fruits').length;
// => 1
```

#### .parentsUntil([selector][,filter])

获取当前匹配元素集里面，每个元素的祖先，但不包括由选择器，DOM 节点或 cheerio 对象匹配的元素。

```js
$('.orange').parentsUntil('#food').length;
// => 1
```

#### .closest(selector)

对于集合中的每个元素，通过测试元素本身，和遍历 DOM 树中的祖先，来获取与选择器匹配的第一个元素。

```js
$('.orange').closest();
// => []
$('.orange').closest('.apple');
// => []
$('.orange').closest('li');
// => [<li class="orange">Orange</li>]
$('.orange').closest('#fruits');
// => [<ul id="fruits"> ... </ul>]
```

#### .next([selector])

获取第一个选定元素的下一个兄弟，可选择让选择器过滤。

```js
$('.apple')
  .next()
  .hasClass('orange');
//=> true
```

#### .nextAll([selector])

获取第一个选定元素的，所有兄弟节点，可选择让选择器过滤。

```js
$('.apple').nextAll();
//=> [<li class="orange">Orange</li>, <li class="pear">Pear</li>]
$('.apple').nextAll('.orange');
//=> [<li class="orange">Orange</li>]
```

#### .nextUntil([selector], [filter])

获取以下所有兄弟节点，但不包括选择器匹配的元素，可选择让另一个选择器过滤。

```js
$('.apple').nextUntil('.pear');
//=> [<li class="orange">Orange</li>]
```

#### .prev([selector])

获取第一个选定元素的前一个兄弟，可选择让选择器过滤。

```js
$('.orange')
  .prev()
  .hasClass('apple');
//=> true
```

#### .prevAll([selector])

获取第一个选定元素的，所有前面兄弟节点，可选择让选择器过滤。

```js
$('.pear').prevAll();
//=> [<li class="orange">Orange</li>, <li class="apple">Apple</li>]
$('.pear').prevAll('.orange');
//=> [<li class="orange">Orange</li>]
```

#### .prevUntil([selector], [filter])

获取所有前面的兄弟，但不包括选择器匹配的元素，可选择让另一个选择器过滤。

```js
$('.pear').prevUntil('.apple');
//=> [<li class="orange">Orange</li>]
```

#### .slice( start, [end] )

获取，指定范围匹配的元素

```js
$('li')
  .slice(1)
  .eq(0)
  .text();
//=> 'Orange'

$('li').slice(1, 2).length;
//=> 1
```

#### .siblings([selector])

获取第一个选定元素的兄弟，不包括它自己。

```js
$('.pear').siblings().length;
//=> 2

$('.pear').siblings('.orange').length;
//=> 1
```

#### .children([selector])

获取第一个选定元素的子元素。

```js
$('#fruits').children().length;
//=> 3

$('#fruits')
  .children('.pear')
  .text();
//=> Pear
```

#### .contents()

获取匹配元素集里面，每个元素的子元素，包括文本和注释节点。

```js
$('#fruits').contents().length;
//=> 3
```

#### .each( function(index, element) )

迭代一个 cheerio 对象，为每个匹配的元素执行一个函数。当触发回调时，该函数会在 DOM 元素的上下文中触发，因此`this`指当前元素，它等效于函数参数`element`。要早点打破了`each`循环，返回`false`就行。

```js
const fruits = [];

$('li').each(function(i, elem) {
  fruits[i] = $(this).text();
});

fruits.join(', ');
//=> Apple, Orange, Pear
```

#### .map( function(index, element) )

通过函数传递当前匹配集里面的，每个元素，生成包含返回值的新 Cheerio 对象。该函数可以返回单个数据项或数据项数组，插回结果集里面。如果返回数组，则将数组内的元素，插入到集合中。如果函数返回 null 或 undefined，则不会插入任何元素。

```js
$('li')
  .map(function(i, el) {
    // this === el
    return $(this).text();
  })
  .get()
  .join(' ');
//=> "apple orange pear"
```

#### .filter( selector ) <br /> .filter( selection ) <br /> .filter( element ) <br /> .filter( function(index, element) )

迭代一个 cheerio 对象，将选择器元素集，筛选与选择器匹配的元素或传递函数的测试。指定 Cheerio selection 时，仅返回该选择中，包含的元素。指定 element 时，仅返回该元素（如果它包含在原始选择中）。如果使用函数方法，则在所选元素的上下文中，执行该函数，因此`this`指当前元素。

选择器：

```js
$('li')
  .filter('.orange')
  .attr('class');
//=> orange
```

函数：

```js
$('li')
  .filter(function(i, el) {
    // this === el
    return $(this).attr('class') === 'orange';
  })
  .attr('class');
//=> orange
```

#### .not( selector ) <br /> .not( selection ) <br /> />.not（function（index，elem））

从匹配元素集里面，删除元素。给出一个，表示一组 DOM 元素的 jQuery 对象的话，`.not()`方法会从匹配元素的子集中，构造新的 jQuery 对象。提供的选择器针对每个元素进行测试; 与选择器不匹配的元素，将包含在结果中。该`.not()`方法与`.filter()`一样，可以用个函数作为它的参数。函数返回 true 的元素，将从过滤集里面排除; 所有其他元素就会包括。

选择器：

```js
$('li').not('.apple').length;
//=> 2
```

函数：

```js
$('li').not(function(i, el) {
  // this === el
  return $(this).attr('class') === 'orange';
}).length;
//=> 2
```

#### .has( selector ) <br /> .has( element )

过滤匹配元素集合，仅留下，有 DOM 匹配元素后代，或与给定选择器匹配的后代元素。相当于`.filter(':has(selector)')`。

选择器：

```js
$('ul')
  .has('.pear')
  .attr('id');
//=> fruits
```

元素：

```js
$('ul')
  .has($('.pear')[0])
  .attr('id');
//=> fruits
```

#### .first()

将选择 cheerio 对象的第一个元素

```js
$('#fruits')
  .children()
  .first()
  .text();
//=> Apple
```

#### .last()

将选择 cheerio 对象的最后一个元素

```js
$('#fruits')
  .children()
  .last()
  .text();
//=> Pear
```

#### .eq( i )

将匹配元素集，指定为索引处的元素集。使用`.eq(-i)`，会最后的元素，向前计数。

```js
$('li')
  .eq(0)
  .text();
//=> Apple

$('li')
  .eq(-1)
  .text();
//=> Pear
```

#### .get( [i] )

检索由 Cheerio 对象匹配的 DOM 元素。如果指定了索引，则检索 Cheerio 对象匹配的其中一个元素：

```js
$('li').get(0).tagName;
//=> li
```

如果未指定索引，则检索 Cheerio 对象匹配的所有元素：

```js
$('li').get().length;
//=> 3
```

#### .index()

#### .index( selector )

#### .index( nodeOrSelection )

从匹配的元素中，搜索给定元素。

```js
$('.pear').index();
//=> 2
$('.orange').index('li');
//=> 1
$('.apple').index($('#fruit, li'));
//=> 1
```

#### .end()

当前(工作)链中，结束最近的过滤操作，并将匹配元素集返回到先前的状态。

```js
$('li')
  .eq(0)
  .end().length;
//=> 3
```

#### .add( selector [, context] )

#### .add( element )

#### .add( elements )

#### .add( html )

#### .add( selection )

将元素添加到匹配元素集。

```js
$('.apple').add('.orange').length;
//=> 2
```

#### .addBack( [filter] )

将栈上的前一组元素，添加到当前集合，可选择让选择器过滤。

```js
$('li')
  .eq(0)
  .addBack('.orange').length;
//=> 2
```

### 操纵

修改 DOM 结构的方法。

#### .append( content, [content, ...] )

插入内容作为，每个选定元素的*最后*子元素。

```js
$('ul').append('<li class="plum">Plum</li>');
$.html();
//=>  <ul id="fruits">
//      <li class="apple">Apple</li>
//      <li class="orange">Orange</li>
//      <li class="pear">Pear</li>
//      <li class="plum">Plum</li>
//    </ul>
```

#### .appendTo( target )

将匹配元素集里面的，每个元素插入到 target 的末尾。

```js
$('<li class="plum">Plum</li>').appendTo('#fruits');
$.html();
//=>  <ul id="fruits">
//      <li class="apple">Apple</li>
//      <li class="orange">Orange</li>
//      <li class="pear">Pear</li>
//      <li class="plum">Plum</li>
//    </ul>
```

#### .prepend( content, [content, ...] )

插入内容作为，每个选定元素的 _第一个_ 子元素。

```js
$('ul').prepend('<li class="plum">Plum</li>');
$.html();
//=>  <ul id="fruits">
//      <li class="plum">Plum</li>
//      <li class="apple">Apple</li>
//      <li class="orange">Orange</li>
//      <li class="pear">Pear</li>
//    </ul>
```

#### .prependTo( target )

将匹配元素集里面的，每个元素插入到 target 的开头。

```js
$('<li class="plum">Plum</li>').prependTo('#fruits');
$.html();
//=>  <ul id="fruits">
//      <li class="plum">Plum</li>
//      <li class="apple">Apple</li>
//      <li class="orange">Orange</li>
//      <li class="pear">Pear</li>
//    </ul>
```

#### .after( content, [content, ...] )

在匹配元素集里面的，每个元素旁边插入内容。

```js
$('.apple').after('<li class="plum">Plum</li>');
$.html();
//=>  <ul id="fruits">
//      <li class="apple">Apple</li>
//      <li class="plum">Plum</li>
//      <li class="orange">Orange</li>
//      <li class="pear">Pear</li>
//    </ul>
```

#### .insertAfter( target )

在 target 之后，插入匹配元素集里面的，每个元素。

```js
$('<li class="plum">Plum</li>').insertAfter('.apple');
$.html();
//=>  <ul id="fruits">
//      <li class="apple">Apple</li>
//      <li class="plum">Plum</li>
//      <li class="orange">Orange</li>
//      <li class="pear">Pear</li>
//    </ul>
```

#### .before( content, [content, ...] )

在匹配元素集里面的，每个元素之前，插入内容。

```js
$('.apple').before('<li class="plum">Plum</li>');
$.html();
//=>  <ul id="fruits">
//      <li class="plum">Plum</li>
//      <li class="apple">Apple</li>
//      <li class="orange">Orange</li>
//      <li class="pear">Pear</li>
//    </ul>
```

#### .insertBefore( target )

在 target 之前，插入匹配元素集里面的，每个元素。

```js
$('<li class="plum">Plum</li>').insertBefore('.apple');
$.html();
//=>  <ul id="fruits">
//      <li class="plum">Plum</li>
//      <li class="apple">Apple</li>
//      <li class="orange">Orange</li>
//      <li class="pear">Pear</li>
//    </ul>
```

#### .remove( [selector] )

删除 DOM 及其所有子项中的匹配元素集。`selector`过滤要删除的匹配元素集。

```js
$('.pear').remove();
$.html();
//=>  <ul id="fruits">
//      <li class="apple">Apple</li>
//      <li class="orange">Orange</li>
//    </ul>
```

#### .replaceWith( content )

用`content`替换匹配的元素。

```js
const plum = $('<li class="plum">Plum</li>');
$('.pear').replaceWith(plum);
$.html();
//=> <ul id="fruits">
//     <li class="apple">Apple</li>
//     <li class="orange">Orange</li>
//     <li class="plum">Plum</li>
//   </ul>
```

#### .empty()

清空元素，删除所有子元素。

```js
$('ul').empty();
$.html();
//=>  <ul id="fruits"></ul>
```

#### .html( [htmlString] )

从第一个选定元素，获取 html 内容字符串。如果`htmlString`指定了，则每个选定元素的内容，将替换为新内容。

```js
$('.orange').html();
//=> Orange

$('#fruits')
  .html('<li class="mango">Mango</li>')
  .html();
//=> <li class="mango">Mango</li>
```

#### .text( [textString] )

获取匹配元素集里面，每个元素的文本内容组合，包括它们的后代。如果`textString`指定，则每个选定元素的内容，将替换为新文本内容。

```js
$('.orange').text();
//=> Orange

$('ul').text();
//=>  Apple
//    Orange
//    Pear
```

#### .wrap( content )

该 `.wrap`函数可以接受，任何能传递给\$()工厂函数的字符串或对象，用来指定 DOM 结构。这个结构可以嵌套几层深，但应该只包含一个 inmost 元素。此结构的副本，会包裹住匹配元素集，每个元素都会进行包装。此方法返回，已改装的原始元素集。

```js
const redFruit = $('<div class="red-fruit"></div>');
$('.apple').wrap(redFruit);

//=> <ul id="fruits">
//     <div class="red-fruit">
//      <li class="apple">Apple</li>
//     </div>
//     <li class="orange">Orange</li>
//     <li class="plum">Plum</li>
//   </ul>

const healthy = $('<div class="healthy"></div>');
$('li').wrap(healthy);

//=> <ul id="fruits">
//     <div class="healthy">
//       <li class="apple">Apple</li>
//     </div>
//     <div class="healthy">
//       <li class="orange">Orange</li>
//     </div>
//     <div class="healthy">
//        <li class="plum">Plum</li>
//     </div>
//   </ul>
```

#### .css( [propertyName] ) <br /> .css( [ propertyNames] ) <br /> .css( [propertyName], [value] ) <br /> .css( [propertyName], [function] ) <br /> .css( [properties] )

获取匹配元素集里面，第一个元素的样式属性值，或为每个匹配元素设置一个或多个 CSS 属性。

### 渲染

当您准备好渲染文档时，您可以使用实用函数`html`：

```js
$.html();
//=>  <ul id="fruits">
//      <li class="apple">Apple</li>
//      <li class="orange">Orange</li>
//      <li class="pear">Pear</li>
//    </ul>
```

如果要返回 outerHTML，可以使用`$.html(selector)`：

```js
$.html('.pear');
//=> <li class="pear">Pear</li>
```

默认情况下，`html`会留下一些标签。有时您可能希望呈现有效的 XML 文档。例如，您可以解析以下 XML 代码段：

```xml
const $ = cheerio.load('<media:thumbnail url="http://www.foo.com/keyframe.jpg" width="75" height="50" time="12:05:01.123"/>');
```

...以 后想要渲染到 XML。为此，您可以使用'xml'实用程序函数：

```js
$.xml();
//=>  <media:thumbnail url="http://www.foo.com/keyframe.jpg" width="75" height="50" time="12:05:01.123"/>
```

您还可以使用。渲染 Cheerio 对象的文本内容，通过静态方法`text`就行：

```js
const $ = cheerio.load('This is <em>content</em>.');
$.text();
//=> This is content.
```

可以通过 Cheerio 模块本身，调用该方法 - 确保传递的是节点集合！

```js
const $ = cheerio.load('<div>This is <em>content</em>.</div>');
cheerio.text($('div'));
//=> This is content.
```

### 杂项

DOM 元素方法，不适合其他任何地方

#### .toArray()

将 jQuery 集里面包含的所有 DOM 元素，转为数组。

```js
$('li').toArray();
//=> [ {...}, {...}, {...} ]
```

#### .clone()

克隆 cheerio 对象。

```js
const moreFruit = $('#fruits').clone();
```

### 工具箱

#### \$.root

有时您需要使用顶级根元素。要查询它，您可以使用`$.root()`。

```js
$.root()
  .append('<ul id="vegetables"></ul>')
  .html();
//=> <ul id="fruits">...</ul><ul id="vegetables"></ul>
```

#### \$.contains( container, contained )

检查`contained`DOM 元素是否为`container`DOM 元素的后代。

#### \$.parseHTML( data [, context ][, keepscripts ] )

将字符串解析为 DOM 节点数组。该`context`参，数对 Cheerio 没有意义，但它是为了兼容 API 而维护的。

#### \$.load( html[, options ] )

加载 HTML。（有关详细信息，请参阅上一节标题为“加载”。）

### 插件

一旦加载文档后，您可以扩展原型，或等效`fn`属性，使用自定义插件方法：

```js
const $ = cheerio.load('<html><body>Hello, <b>world</b>!</body></html>');
$.prototype.logHtml = function() {
  console.log(this.html());
};

$('body').logHtml(); // logs "Hello, <b>world</b>!" to the console
```

### “DOM Node”对象

Cheerio 所制造的对象，与[基于浏览器的 DOM 节点](https://developer.mozilla.org/en-US/docs/Web/API/Node)有许多相似之处。所以，您可以期望它们定义了以下属性：

- `tagName`
- `parentNode`
- `previousSibling`
- `nextSibling`
- `nodeValue`
- `firstChild`
- `childNodes`
- `lastChild`

## 视频讲解

<http://vimeo.com/31950192>

> 这个视频教程是 Nettut 的“如何使用 Node.js 和 jQuery 抓取网页”的后续内容，使用 cheerio 而不是 JSDOM + jQuery。这个视频展示了使用 cheerio 是多么容易，以及 cheerio 比 JSDOM + jQuery 快多少。

## 贡献者

这些是贡献者，让 cheerio 成为可能的人：

```
project  : cheerio
 repo age : 2 years, 6 months
 active   : 285 days
 commits  : 762
 files    : 36
 authors  :
   293  Matt Mueller            38.5%
   133  Matthew Mueller         17.5%
    92  Mike Pennisi            12.1%
    54  David Chambers          7.1%
    30  kpdecker                3.9%
    19  Felix Böhm             2.5%
    17  fb55                    2.2%
    15  Siddharth Mahendraker   2.0%
    11  Adam Bretz              1.4%
     8  Nazar Leush             1.0%
     7  ironchefpython          0.9%
     6  Jarno Leppänen         0.8%
     5  Ben Sheldon             0.7%
     5  Jos Shepherd            0.7%
     5  Ryan Schmukler          0.7%
     5  Steven Vachon           0.7%
     4  Maciej Adwent           0.5%
     4  Amir Abu Shareb         0.5%
     3  jeremy.dentel@brandingbrand.com 0.4%
     3  Andi Neck               0.4%
     2  steve                   0.3%
     2  alexbardas              0.3%
     2  finspin                 0.3%
     2  Ali Farhadi             0.3%
     2  Chris Khoo              0.3%
     2  Rob Ashton              0.3%
     2  Thomas Heymann          0.3%
     2  Jaro Spisak             0.3%
     2  Dan Dascalescu          0.3%
     2  Torstein Thune          0.3%
     2  Wayne Larsen            0.3%
     1  Timm Preetz             0.1%
     1  Xavi                    0.1%
     1  Alex Shaindlin          0.1%
     1  mattym                  0.1%
     1  Felix Böhm            0.1%
     1  Farid Neshat            0.1%
     1  Dmitry Mazuro           0.1%
     1  Jeremy Hubble           0.1%
     1  nevermind               0.1%
     1  Manuel Alabor           0.1%
     1  Matt Liegey             0.1%
     1  Chris O'Hara            0.1%
     1  Michael Holroyd         0.1%
     1  Michiel De Mey          0.1%
     1  Ben Atkin               0.1%
     1  Rich Trott              0.1%
     1  Rob "Hurricane" Ashton  0.1%
     1  Robin Gloster           0.1%
     1  Simon Boudrias          0.1%
     1  Sindre Sorhus           0.1%
     1  xiaohwan                0.1%
```

## Cheerio 在现实世界中

你在生产中，使用 cheerio 吗？把它添加到[wiki](https://github.com/cheeriojs/cheerio/wiki/Cheerio-in-Production)！

## 测试

要运行测试套件，请下载存储库，然后在 cheerio 目录中，运行：

```shell
make setup
make test
```

这将下载开发包，并运行测试套件。

## 特别谢谢

这个库站在一些令人难以置信的开发人员的肩膀上。特别感谢：

**•@FB55 for node-htmlparser2＆CSSSelect：**Felix 有编写快速解析引擎的诀窍。他完全重写了@ tautologistic 的`node-htmlparser`和@harry 的`node-soupselect`，从头开始，使他们两个更快，更灵活。没有他的基础工作，Cheerio 是不可能的

**•@jQuery jQuery 团队：**核心 API 是同类产品中最好的，尽管需要处理了，所有浏览器的不一致性，但代码库非常干净且易于理解。cheerio 的大部分实现和文档来自 jQuery。多谢你们。

**•@visionmedia：**这个库的风格，结构，开源“性”，来自于研究 TJ 的风格和使用他的许多库。这个家伙不断推出高质量的库，并且一直非常愿意帮助或回答问题。很摇滚啊， TJ。

## 执照

MIT
