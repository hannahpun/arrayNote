# Array
這一堂課就是介紹一些 Array 方法，其實陣列技巧常常用到。索性把它全部整理出來讓自己以後也可以快速搜尋。

#### 初始值
```
 const inventors = [
      { first: 'Albert', last: 'Einstein', year: 1879, passed: 1955 },
      { first: 'Isaac', last: 'Newton', year: 1643, passed: 1727 },
      { first: 'Galileo', last: 'Galilei', year: 1564, passed: 1642 },
      { first: 'Marie', last: 'Curie', year: 1867, passed: 1934 },
      { first: 'Johannes', last: 'Kepler', year: 1571, passed: 1630 },
      { first: 'Nicolaus', last: 'Copernicus', year: 1473, passed: 1543 },
      { first: 'Max', last: 'Planck', year: 1858, passed: 1947 },
      { first: 'Katherine', last: 'Blodgett', year: 1898, passed: 1979 },
      { first: 'Ada', last: 'Lovelace', year: 1815, passed: 1852 },
      { first: 'Sarah E.', last: 'Goode', year: 1855, passed: 1905 },
      { first: 'Lise', last: 'Meitner', year: 1878, passed: 1968 },
      { first: 'Hanna', last: 'Hammarström', year: 1829, passed: 1909 }
    ];
```

## Basic Array Method
#### 初始值
```
    const colors = ['red', 'yellow', 'blue'];
```
* Array.prototype.push(elementN)  
在原本的陣列 **後面** 加上新值，他會回傳 length ，所以把 push 存在 變數裡 (newColor) 他竟然是會回傳陣列長度 Number 呢!  
另外 const 不能被重新指定值但 colors.push　但在這裡卻不會有錯誤，為什麼呢？　因為 array 跟 Object 都是 by reference 只要不是重新指定 ( = ) 就會在同一個 reference 裡
```
    const newColor = colors.push('purple', 'green');

    console.log(colors) // ['red', 'yellow', 'blue', 'purple', 'green']
    console.log(newColor) // 5
```
* Array.prototype.unshift(elementN)
在原本的陣列 **前面** 加上新值，會回傳 length
```
    const newColor = colors.unshift('purple', 'green');

    console.log(colors) // ['purple', 'green', 'red', 'yellow', 'blue' ]
    console.log(newColor) // 5
```
* Array.prototype.pop()
移除原本陣列 **最後面** 的第一個值，回傳被移除掉的那個值
```
    const newColor = colors.pop();

    console.log(colors) // ['red', 'yellow']
    console.log(newColor) // 'blue'
```
* Array.prototype.shift()
移除原本陣列 **最前面** 的第一個值，回傳被移除掉的那個值
```
    const newColor = colors.shift();

    console.log(colors) // ['yellow', 'blue' ]
    console.log(newColor) // 'red'
```

* concat


## Filter somthing
* Array.prototype.find(item, index, array)
* Array.prototype.filter(item, index, array)
* Array.prototype.forEach(item, index, array)
* Array.prototype.map(item, index, array)
* Array.prototype.some(item, index, array)
* Array.prototype.every(item, index, array)


## Special
* Array.prototype.reduce(accumulator, currentValue, currentIndex, array [, initialValue])

## Order
* Array.prototype.sort(a, b)
* Array.prototype.reverse()

## Operation
* 

## add or remove some item in Array
* slice
* indexOf
* join
* splice
* [include](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/includes)



### Reference
* [javaScript 陣列處理方法](https://wcc723.github.io/javascript/2017/06/29/es6-native-array/#Array-prototype-forEach)