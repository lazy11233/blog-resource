---
title: JavaScript数组方法简介
date: 2018-10-31 14:26:13
thumbnail: http://phgcrbrst.bkt.clouddn.com/array02.jpg
categories:
- [JavaScript]
tags:
- JavaScript
- Array api
- 不适合人类阅读
---
(本文可能不适合人类阅读，只是简单的复制粘贴)
本文介绍了` JavaScript `数组常用的方法。
<!-- more -->

## 不会改变原来数组本身

### concat()

`concat()`方法将传入的数组或者元素与原数组合并，组成一个新的数组并返回。

```javascript
const arr = [1, 2, 3];
const arr2 = arr.concat([4, [5, 6], [7, [8, 9]]]);
console.log(arr2); // [1, 2, 3, 4, [5, 6],[7, [8, 9]]]
console.log(arr); // [1, 2, 3]
```

如果`concat`方法中不传入任何参数，name将与机遇原数组**浅复制**生成一个一模一样的数组。

```javascript
const array = [1, 2, 3];
const array2 = array.concat();
console.log(array === array2); // false
console.log(array[0] === array2[0]); // true
```

### every()

`every()`方法使用传入的函数测试所有元素，只要其中一个函数返回为`false`，那么该方法的结果为`false`；否则返回`true`。

```javascript
const arr = [1, 23, 45, 657, 8756, 85, 534, 7567, 4125];
const rlt = arr.every(item => item % 2 === 0);
console.log(rlt); // false
```

### some()

`some()`方法使用传入函数测试是不是有部分满足。只要有一个函数返回值为true，则该方法返回`true`

```javascript
const arr = [1, 23, 45, 657, 8756, 85, 534, 7567, 4125];
const rlt = arr.some(item => item % 2 === 0);
console.log(rlt); // true
```

### filter()

`filter()`方法使用传入的函数测试所有元素，并返回所有通过测试的元素组成的新数组。它好比一个过滤器，筛掉不符合条件的元素。

```javascript
const arr = [1, 23, 45, 657, 8756, 85, 534, 7567, 4125];
const rlt = arr.filter(item => item % 2 === 0);
console.log(rlt); // [8756, 534]
```

### indexOf()

`indexOf()`方法用于查找元素在数组中第一次出现时的索引，如果没有，则返回-1

`indexOf()`使用严格相等（即使用`===`去匹配数组中的元素）。

```javascript
var array = ['abc', 'def', 'ghi','123'];
console.log(array.indexOf('def')); // 1
console.log(array.indexOf('def',-1)); // -1 此时表示从最后一个元素往后查找,因此查找失败返回-1
console.log(array.indexOf('def',-4)); // 1 由于4大于数组长度,此时将查找整个数组,因此返回1
console.log(array.indexOf(123)); // -1, 由于是严格匹配,因此并不会匹配到字符串'123'
```

### join()

`join()`方法将数组中的所有元素连接成一个字符串。如果`join()`方法不传入参数，缺省默认为逗号。

```javascript
const arr = [1, 2, 3];
const rlt = arr.join('3');
console.log(arr); // [1, 2, 3]
console.log(rlt); // 13233
const rlt2 = arr.join();
console.log(rlt2); // 1,2,3
```

### map()

`marp()`方法遍历数组，使用传入函数处理每个元素，并返回函数的返回值组成新的数组。

```javascript
const officers = [
  { id: 20, name: 'Captain Piett' },
  { id: 24, name: 'General Veers' },
  { id: 56, name: 'Admiral Ozzel' },
  { id: 88, name: 'Commander Jerjerrod' },
];
const rlt = officers.map(item => item.id);
console.log(rlt); // [20, 24, 56, 88]
```

### slice()

`slice()`方法将数组中一部分元素**浅复制**存入新的数组对象，并返回这个数组对象。

```javascript
const numbers = ['one', 'two', 'three', 'four', 'five'];
const rlt = numbers.slice(2, 3);
console.log(rlt); // ['three']
const rlt2 = numbers.slice();
console.log(rlt2); // ['one', 'two', 'three', 'four', 'five']
```

### reduce()

`reduce()`方法接受一个函数作为累加器，数组中的每个值（从左向右）开始合并，最终为一个值。

```javascript
const array = ['h', 'ello', 'worl', 'd'];
const rlt = array.reduce((p, v) => p + v);
console.log(rlt); // 'helloeworld'
```

## 会改变数组本身的方法
### pop()

`pop()`方法删除一个数组中的最后一个元素，并且返回这个元素。

```javascript
const arr1 = ['刘备', '关羽', '张飞'];
const popItem = arr1.pop();
console.log(popItem); // '张飞'
console.log(arr1); // ['刘备', '关羽']
```

### push()

`push()`方法添加一个或者多个元素到数组末尾，并且返回数组新的长度。

```javascript
const arr2 = ['刘备', '关羽', '张飞'];
const pushItem = arr2.push('赵云');
console.log(pushItem);// 4
console.log(arr2);// ['刘备', '关羽', '张飞', '赵云']
```

### shift()

`shift()`方法删除数组的第一个元素，并返回这个删除的元素。“栈底弹出”

```javascript
const arr3 = ['刘备', '关羽', '张飞'];
const shiftItem = arr3.shift();
console.log(arr3);// ['关羽', '张飞']
console.log(shiftItem); // '刘备'
```

### unshift()

`unshift()`方法用于在数组开始处插入一些元素，并数组新的长度。“栈底插入”

```javascript
const arr4 = ['刘备', '关羽', '张飞'];
const unshiftRlt = arr4.unshift('诸葛亮');
console.log(arr4);// ["诸葛亮", "刘备", "关羽", "张飞"]
console.log(unshiftRlt);// 4
```

### reverse()

`reverse()`方法颠倒数组元素中的位置，第一个会成为最后一个，并返回对该数组的饮用。

```javascript
const arr5 = ['刘备', '关羽', '张飞'];
const reverseRlt = arr5.reverse();
console.log(arr5);// ["张飞", "关羽", "刘备"]
console.log(reverseRlt);// 4
console.log(arr5 === reverseRlt);// true
```

### sort()

`sort()`方法对数组元素进行排序，并返回这个数组。

```javascript
const arr6 = [1, 324, 53, 6341, 415, 67785, 857, 3413];
const sortRlt = arr6.sort();
console.log(arr6);// [1, 324, 3413, 415, 53, 6341, 67785, 857]
console.log(sortRlt);// [1, 324, 3413, 415, 53, 6341, 67785, 857]
console.log(arr6 === sortRlt);// true
```

可以为`sort()`方法指定排序方式，比如：

```javascript
const arr7 = [1, 324, 53, 6341, 415, 67785, 857, 3413];
const sortRlt2 = arr7.sort((a, b) => b - a);
console.log(sortRlt2);// [67785, 6341, 3413, 857, 415, 324, 53, 1]
```

使用映射改善排序

```javascript
// 需要被排序的数组
const array = ['dog', 'Cat', 'Boy', 'apple'];
// 对需要排序的数字和位置的临时存储
const mapped = array.map((el, i) => ({ index: i, value: el.toLowerCase() }));
// 按照多个值排序数组
mapped.sort((a, b) => +(a.value > b.value) || +(a.value === b.value) - 1);
// 根据索引得到排序的结果
const result = mapped.map((el) => array[el.index]);
console.log(result); // ["apple", "Boy", "Cat", "dog"]
```

### splice()

`splice()`方法使用新元素替换旧元素的方式来修改数组。

语法：`arr.splice(start,deleteCount[, item1,item2])`

`start`指定从哪一位开始修改内容。如果超过了数组长度，则从数组末尾开始添加内容；如果是负值，则其指定的索引位置等同于`length + start`(length为数组长度)，表示从数组末尾开始的第`-start`位

`deleteCount`指定要删除的元素个数，如果等于0，表示不删除。这种情况下，至少应该添加一位新元素，若大于start之后的元素总和，则start及之后的元素都将被删除。

`itemN`指定新增的元素，如果缺省，则该方法只删除数组元素。

返回值 由数组中被删除元素组成的数组，如果没有删除，则返回一个空数组。

```javascript
let animal = ['dog', 'Cat', 'Boy', 'apple'];
let splices = animal.splice(1, 1); // 从数组的下标1开始删除，删除一位
console.log(splices);// ['Cat']
console.log(animal);// ["dog", "Boy", "apple"]

animal = ['dog', 'Cat', 'Boy', 'apple'];
splices = animal.splice(animal.length, 1, 'Meow'); // start大于数组长度，则从末尾开始添加元素
console.log(animal); // ["dog", "Cat", "Boy", "apple", "Meow"]
console.log(splices); // []

animal = ['dog', 'Cat', 'Boy', 'apple'];
splices = animal.splice(-2, 1, 'Meow'); // start为负数，从数组的-start开始删除，替换
console.log(animal);
console.log(splices);

animal = ['dog', 'Cat', 'Boy', 'apple'];
splices = animal.splice(-10, 1, 'Meow'); // -start超出数组长度，默认从首位开始删除
console.log(animal); // ["Meow", "Cat", "Boy", "apple"]
console.log(splices); // ["dog"]

animal = ['dog', 'Cat', 'Boy', 'apple'];
splices = animal.splice(0, 10); // deleteCount 大于数start之后的长度时，将start之后的数据全部删除。
console.log(animal); // []
console.log(splices); // ["dog", "Cat", "Boy", "apple"]
```
