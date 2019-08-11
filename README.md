# Personal-Tests-Collection
> 道阻且长，弄懂一个是一个
>



## 题源

- [JavaScript进阶仓库](https://github.com/lydiahallie/javascript-questions/blob/master/zh-CN/README-zh_CN.md)
- [The Blog of David Shariff - 经典Js20题](http://davidshariff.com/js-quiz/)
- [前端开发面试题大收集](https://fe.padding.me/#/)
- [我的牛客网收藏题](https://www.nowcoder.com/profile/457362991/myFollowings)
- [我的掘金收藏集](https://juejin.im/collection/5cf216516fb9a069f422422c)



## 知识点

- [前端面试之道 - Interview Map](http://caibaojian.com/interview-map/frontend/)
- [慕课Wiki词典-Js](https://wiki.imooc.com/javascript/index.html)



## 分类

> 待补充



## Get Start

#### 1.   打印输出什么？

```javascript
function sayHi () {
    console.log(name)
    console.log(age)
    var name = 'xiaoqiang'
    let age = 21
}
sayHi()
```

- A: `Lydia` 和 `undefined`
- B: `Lydia` 和 `ReferenceError`
- C: `ReferenceError` 和 `21`
- D: `undefined` 和 `ReferenceError`

<details>
<summary><strong>答案</strong></summary>
    <strong>选择：D</strong>
    <p><strong>笔点：</strong><span>let与var的区别</span> </p>
    <strong>解析：</strong>
    <p>输出name为<code>undefined</code>：对于用var声明的变量name，在其声明之前使用输出 未定义(undefined)，相当于在打印时先<code>var name</code>后<code>name = 'xiaoqiang'</code></p>
    <p>输出age为<code>ReferenceError</code>：对于用let声明的变量age，在其声明之前使用，输出 引用错误(ReferenceError)，代表当一个不存在的变量被引用时报的错误。在ES6中明确规定变量必须声明后再使用，一切在声明前使用的变量都会报此错误</p>
</details>

<details>
 <summary><strong>笔记</strong></summary>
    <p>
        <strong>var：</strong>有变量提升（内存空间在创建阶段就被设置好了，直到程序运行到定义变量位置之前默认值都是 undefined。）
    </p>
    <p>
        <strong>let：</strong>也有变量提升，和 var 不同，它们不会被初始化。在我们声明（初始化）之前是不能访问它们的。这个行为被称之为暂时性死区。当我们试图在声明之前访问它们时，JavaScript 将会抛出一个 ReferenceError 错误。
    </p>
    <p>
        <strong>再次注意：</strong>1.let,const 有变量提升
        2.let,const的变量提升标注了暂时性死区的开始 
        3.你在暂时性死区里使用,就会报错
    </p>
</details>
---

#### 2. 弹出true还是false？

```javascript
[] == ![] ? alert(true):alert(false)
```

<details>
<summary><strong>答案</strong></summary>
    <strong>结果：true</strong>
    <p><strong>笔点：</strong><span>类型转换(隐式类型转换)</span> </p>
    <p><strong>解析：</strong></p>     
<p>1. 取非！的优先级比==高,  ![] => !true => false</p>  
<p>2. 等号左边是引用类型 [] => [].toPrimitive()=''   </p>
<p>3. '' == false   =>   Number('') == Number(false)   </p>
<p>4. 0 == 0 => true   </p>
    </details>

<details>
 <summary><strong>笔记</strong></summary>
    <p>
        <strong>取经：</strong> <a src='https://segmentfault.com/a/1190000008594792'>==  如何工作的？</a>and <a img='https://github.com/jawil/blog/issues/1'>各种蛋疼的类型转换</a>
    </p>
    <p>
        <strong>简单来说：</strong>
        在 == 符号的左右，遇到布尔类型、字符串类型和数字类型这三种基本类型，通通会`Number(x)`将其转为数字；若有一边是引用类型有一边是基本类型，则将引用类型`ToPromitive(x)`后再与另一边的数字类型做比较；若都是引用类型则看他们的指针是否指向同一个对象，是则true；(你需要弄懂ToPrimitive()的执行原理)
    </p>
    <p>
        <strong>注意事项：</strong> 时刻牢记，只有`null undefined 空字符串 NaN 0 `会被转换为false，其他的都将转为true；null与undefined不严格相等；NaN与谁都不想等包括自身；null转数字为0，而undefined转数字为NaN
    </p>
</details>

---

