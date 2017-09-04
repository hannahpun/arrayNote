# Array
這一堂課就是介紹一些 Array 方法，其實陣列技巧常常用到。索性把它全部整理出來讓自己以後也可以快速搜尋。
每一個小單元都有一個初始值，這樣就不用每一個範例都重覆貼上了。花了很多時間整理希望對自己跟路過的人有幫助


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

* Array.prototype.concat()  
把兩個陣列合併在一起，並回傳新陣列
```
    const colors2 = ['grey', 'black', 'white'];
    const newColor = colors.concat(colors2);

    console.log(colors) // ['red', 'yellow', 'blue'] 原本的
    console.log(newColor) // ['red', 'yellow', 'blue', 'grey', 'black', 'white' ]
```
## Filter somthing
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
* Array.prototype.find(item, index, array)  
回傳一個值，且是**第一個**抓到條件為 true 的值
```
const findEmpty = inventors.find(function(item){
    
})
console.log(findEmpty) // 沒有條件會 undefined

const findInventors = inventors.find(function(item){
    return item.year > 1870;
})
console.log(findInventors) // 有好幾個是 > 1800 的，但他指會回傳第一個抓到的 { first: 'Albert', last: 'Einstein', year: 1879, passed: 1955 }
```
* Array.prototype.filter(item, index, array)  
回傳一個陣列，只要條件為 true 的就會包含在此陣列，適合拿來搜尋 
```
const filterEmpty = inventors.filter(function(item){
    
})
console.log(filterEmpty) // 沒有條件會 undefined

const filterInventors = inventors.filter(function(item){
    return item.year > 1870;
})
console.log(findInventors) // [{first: "Albert", last: "Einstein", year: 1879, passed: 1955}
{first: "Katherine", last: "Blodgett", year: 1898, passed: 1979}, {first: "Lise", last: "Meitner", year: 1878, passed: 1968}]
```
* Array.prototype.forEach(item, index, array)  
forEach 不會回傳任何東西，單純只執行原本陣列裡的事
```
const forEachInventors = inventors.forEach(function(item){
    return item.year > 1870;
})
console.log(forEachInventors) // undefined, 不會 return 東西
inventors.forEach(function(item){
    item.year =  1870;
}) 
console.log(inventors) // 全部 12 個的 year = 1870
```
* Array.prototype.map(item, index, array)  
將條件運算後重新組合回傳一個數量等於 array.length 的陣列
```
const mapInventors = inventors.map(function(item){
    return item.year > 1870;
})
console.log(mapInventors) // [false, false, true ... 12 個]

const mapInventors2 = inventors.map(function(item){
    if(item.year > 1870){
        return `${item.year}歲`;
    }
    return false;
})
console.log(mapInventors2) // ["1879歲", false, false....] 就算是空的還是 false 還是會回傳喔
```
* Array.prototype.some(item, index, array)  
回傳一個值 false/true，只要部分符合就回傳 true
```
const someInventors = inventors.some(function(item){
    return item.year > 1870;
})
console.log(mapInventors) // true
```
* Array.prototype.every(item, index, array)  
回傳一個值 false/true，需要全部符合才回傳 true, 部分符合會回傳 false
```
const everyInventors = inventors.every(function(item){
    return item.year > 1870;
})
console.log(everyInventors) // false
```

## Special
#### 初始值
```
var special = [8, 0, 14];
```
* Array.prototype.reduce(accumulator, currentValue, currentIndex, array [, initialValue])  
回傳運算結果得值．reduce 很特別，他可以與前一個值做運算，先來名詞解釋一下  
accumulator(前一個參數，從 initialValue 開始．若沒有 initialValue 就是從陣列 0 開始) currentIndex(現在的參數) array (全部陣列) initialValue(可以給一個初始值開始)

```
const reduceInventors = inventors.reduce(function(accumulator, currentValue, currentIndex){
    return Math.max(accumulator, currentValue);
})
console.log(reduceInventors) // 14
```
| callback   |      accumulator      |  currentValue |currentIndex |  array | return value
|----------|:-------------:|------:|------:|------:|------:|
| first call |  8 | 0 | 1|[8, 0, 14] | 8
| second call|    8   |   14 |2|[8, 0, 14] |14
```
// 給初始值的狀況  
const reduceInventors2 = inventors.reduce(function(accumulator, currentValue, currentIndex){
    return Math.max(accumulator, currentValue);
},30)
console.log(reduceInventors2) // 30
```
| callback   |      accumulator      |  currentValue |currentIndex |  array | return value
|----------|:-------------:|------:|------:|------:|------:|
| first call |  30 | 8 | 0|[8, 0, 14] | 30
| second call|    30   |   0 |1|[8, 0, 14] |30
| third call|    30   |   12 |2|[8, 0, 14] |30
## Order
* Array.prototype.sort(compareFunction)  
若沒有 compareFunction ，會回傳一個根據 [Unicode](http://jrgraphix.net/r/Unicode/0020-007F) 排序 array.length 長度的 array
```
var fruit = ['cherries', 'apples', 'bananas'];
fruit.sort(); // ['apples', 'bananas', 'cherries']

var scores = [1, 10, 21, 2]; 
scores.sort(); // [1, 10, 2, 21]
//  跟你想的不一樣吧，因為 10 是兩個數字組成，在 unicode 裡 32(數字2） > 31(1 開頭的任何數字)

var things = ['word', 'Word', '1 Word', '2 Words'];
things.sort(); // ['1 Word', '2 Words', 'Word', 'word']
```
若有 compareFunction 會有兩個參數 a / b, Array.prototype.sort(a, b)  
```
function compare(a, b) {
  // 若 a 比較小 排序就是 a, b
  if (a is less than b by some ordering criterion) {
    return -1;
  }
  // 若 a 比較大 排序就是 b, a
  if (a is greater than b by the ordering criterion) {
    return 1;
  }
  // 若一樣
  return 0;
}
```
```
var items = [
  { name: 'Edward', value: 21 },
  { name: 'Sharpe', value: 37 },
  { name: 'And', value: 45 },
  { name: 'The', value: -12 },
  { name: 'Magnetic', value: 13 },
  { name: 'Zeros', value: 37 }
];

// sort by value 快速寫法
items.sort(function (a, b) {
  return a.value - b.value;
});

// sort by name
items.sort(function(a, b) {
  var nameA = a.name.toUpperCase(); // ignore upper and lowercase
  var nameB = b.name.toUpperCase(); // ignore upper and lowercase
  if (nameA < nameB) {
    return -1;
  }
  if (nameA > nameB) {
    return 1;
  }

  // names must be equal
  return 0;
});
```
* Array.prototype.reverse()
相對單純的一個方法，回傳反過來的一個長度為 array.length 的陣列
```
var a = ['one', 'two', 'three'];
var reversed = a.reverse(); 

console.log(a);        // ['three', 'two', 'one']
console.log(reversed); // ['three', 'two', 'one']
```
## Operation
* const my_array = [5, 1, 3, 8, 6, 0]

## get some item in Array
#### 初始值
* Array.prototype.slice(start, end)  
slice 就是切，把 array 頭尾切兩刀。回傳在 start(包含) 跟 end 之間的陣列。經過 slice 後原本陣列不會改變
```
const sliceArray = my_array.slice(2,5);
console.log(sliceArray); // [3, 8, 6]
console.log(my_array); // [5, 1, 3, 8, 6, 0] 不會變
```
Array.prototype.slice(start) 
假如只有一個值就是只切一刀，負數就是從後面切
```
const sliceArray = my_array.slice(2);
console.log(sliceArray); // [3, 8, 6, 0]

const sliceNegativeArray = my_array.slice(-1);
console.log(sliceNegativeArray); // [0]
```
* Array.prototype.splice(start, deleteCount, item1, item2, ...)  
回傳被移掉的值放在陣列裡。splice 乍看下跟 slice 有點像，但其實幾乎完全相反(驚)。slice 是取 start end 裡的東西，而 splice 是 return 中間被移掉的東西。slice 不會影響本來陣列而 splice 就是影響了原本陣列。 新增的 item1, item2 只會影響本來陣列，並不會回傳到新的陣列裡 
splice 是拼接的意思你不但可以切掉某塊還可以塞東西進去。
```
// 假如只有 splice(start)，這時會跟 slice 行為一樣
const spliceArray1 = my_array.splice(3)
console.log(spliceArray1); // [8, 6, 0] 被移掉的值
console.log(my_array); // [5, 1, 3]，index 3 後面都移掉

//一樣可以接受負數
const spliceArray2 = my_array.splice(-1)
console.log(spliceArray2); // [0]
console.log(my_array); // [5, 1, 3, 8, 6] 倒數 1 個後面都移掉

// splice(start, deleteCount 抓幾個) 
const spliceArray3 = my_array.splice(1, 3)
console.log(spliceArray3); // [1, 3, 8] 
console.log(my_array); // [5, 6, 0] 從 index 1 開始抓 3 個 把中間值移掉

// splice(start, deleteCount 抓幾個, 插入 item) 
const spliceArray4 = my_array.splice(1, 3, 'Hana', 'Mike') 
console.log(spliceArray4); // [1, 3, 8] // 不會有 'Hana', 'Mike' 字眼出現
console.log(my_array); // [5, "Hana", "Mike", 6, 0] 從 index 1 開始抓 3 個 把中間值移掉 並塞進 "Hana", "Mike"
```
* Array.prototype.indexOf(searchElement)  
回傳所在位置的 index，如果找不到會回傳 -1
```
const indexArray = my_array.indexOf(3) // 2
console.log(indexArray) // 2
console.log(my_array) // [5, 1, 3, 8, 6, 0]

const indexArray2 = my_array.indexOf(100)
console.log(indexArray) // -1
```
* Array.prototype.join(separator)  
把所有陣列裡的值加上 separator，回傳一個字串
```
const joinArray = my_array.join('-') // 2
console.log(joinArray) // '5-1-3-8-6-0'
console.log(my_array) // [5, 1, 3, 8, 6, 0]

const joinArray2 = my_array.join('') // 2
console.log(joinArray2) // '513860'
```

* Array.prototype.include(searchElement, fromIndex)
看 searchElement 有沒有在 array 裡，回傳 true 或 false
```
const includesArray = my_array.includes(3)
console.log(includesArray) // true
console.log(my_array) // [5, 1, 3, 8, 6, 0]

my_array.includes(5,3) // false 從 index 第三個之後找 5

```

### Reference
* [javaScript 陣列處理方法](https://wcc723.github.io/javascript/2017/06/29/es6-native-array/#Array-prototype-forEach)