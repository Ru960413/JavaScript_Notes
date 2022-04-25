# 常用的 Array methods 整理

以下整理一些常用的 array methods~
待整理的 methods:

## sort()

sort()是一個能幫助我們將 array 中的元素重新排列的方法，會使原本的陣列改變。能夠回傳值是由小到大或是由大到小的陣列，如下：

```js
// 沒有給參數的預設排序
const arr = [5, 9, 1, 3, 2, 6];
arr.sort(); // [1, 2, 3, 5, 6, 9]

// 以匿名函式回參數做「升序」排序
arr.sort(function (a, b) {
  return a - b; // a - b > 0
});
// [1, 2, 3, 5, 6, 9]

// 如果要反過來做「降序」排序
arr.sort(function (a, b) {
  return b - a;
});
// [9, 6, 5, 3, 2, 1]
```

originate from:(看不台懂，需要複習)

```js
const arr = [5, 9, 1, 3, 2, 6];
// 升序
arr.sort(function (a, b) {
  if (a > b) {
    return 1; // 正數時，後面的數放在前面
  } else {
    return -1; // 負數時，前面的數放在前面
  }
});

// 降序
arr.sort(function (a, b) {
  if (a < b) {
    return 1; // 正數時，後面的數放在前面
  } else {
    return -1; // 負數時，前面的數放在前面
  }
});

// 升序 另一種寫法，就會精簡到像最上面那樣！
arr.sort(function (a, b) {
  if (a > b) {
    // a > b  等於 a - b > 0
    return a - b;
  } else {
    return a - b;
  }
});
```

可將字串依長度來排序

```js
const arr = ["hi", "Hello", "Bonjour", "ciao"];
arr.sort(function (a, b) {
  return a.length - b.length;
});

// ["hi", "ciao", "Hello", "Bonjour"]
```

若想要對字串做不區分大小寫的排序則可以用 *toLowerCase()*或 *toUpperCase()*即可～～

## find()

這個方法會回傳第一個符合條件的值，若都不符合則會回傳 undefined。

```js
const array1 = [5, 12, 8, 130, 44];

const found = array1.find((element) => element > 10);

console.log(found);
// 會回傳第一個符合此條條件的值: 12
```

## findIndex()

這個方法會回傳第一個符合條件的值的 index，若無符合的值，則會回傳-1。

```js
const array1 = [5, 12, 8, 130, 44];

const isLargeNumber = (element) => element > 13;

console.log(array1.findIndex(isLargeNumber));
// expected output: 3
//注意：index由0開始計算不是1喔
```

## some()

這個方法會測試 array 中是否*至少有一個*數值符合條件，，若有則 return _true_，若無則 return _false_。

```js
const array = [1, 2, 3, 4, 5];

// checks whether an element is even
const even = (element) => element % 2 === 0;

console.log(array.some(even));
// expected output: true
```

> The some() method does not execute the function for empty array elements.

> The some() method does not change the original array.

## every()

不同於 some()，every()會在確認 array 內的所有值符合條件的狀態下才會 return _true_，否則會 return _false_ 舉例：

```js
const isBelowThreshold = (currentValue) => currentValue < 40;

const array1 = [1, 30, 39, 29, 10, 13];

console.log(array1.every(isBelowThreshold));
// expected output: true
```

例二：

```js
function isBigEnough(element, index, array) {
  return element >= 10;
}
[12, 5, 8, 130, 44].every(isBigEnough); // false
[12, 54, 18, 130, 44].every(isBigEnough); // true
```

## reduce()

_需要 Review 及再閱讀 MDN 文件!_

這個方法可以讓陣列中的每個元素與回傳的值再次作運算，將陣列*reduce*為單一值，常常拿來應用於陣列中每個元素的「累加」或是「比較」。

舉例：

```js
const array1 = [1, 2, 3, 4];

// 0 + 1 + 2 + 3 + 4
const initialValue = 0;
const sumWithInitial = array1.reduce(
  (previousValue, currentValue) => previousValue + currentValue,
  initialValue
);

console.log(sumWithInitial);
// expected output: 10
```

## map()

我們可以用 map()來轉換陣列內的元素，轉換成什麼可由我們決定，以我們想要的方式轉換後，map()會幫我們這些轉換結果，放入另一個新的陣列，回傳回來。

舉例：

```js
const array1 = [1, 4, 9, 16];

// pass a function to map
const map1 = array1.map((x) => x * 2);

console.log(map1);
// expected output: Array [2, 8, 18, 32]
```

_map_ calls a provided callbackFn function once _for each element_ in an array, in order, and _constructs a new array_ from the results. callbackFn is invoked only for indexes of the array which have assigned values (_including undefined_).

例二：

```js
const shoppingCart = [
  { itemName: "Book", price: 220 },
  { itemName: "Bag", price: 350 },
];
const itemNames = shoppingCart.map((x) => x.itemName);
// 只把 itemNames 提取出來
itemNames; // ["Book", "Bag"]

// 把 price 打七九折後提取出來
const discounts = shoppingCart.map((x) => x.price * 0.79);
discounts; // [173.8, 276.5]
```

利用*map()*提取元素和索引的特性，來組合成另一組資料。：

```js
const items = ["book", "cap", "bag"];
const prices = [125, 76, 390];
const listItems = items.map((elem, index) => ({
  itemName: elem,
  price: prices[index],
}));

listItems;
// [{itemName: "book", price: 125},
//  {itemName: "cap", price: 76},
//  {itemName: "bag", price: 390}]
```

const items = ["book", "cap", "bag"];
const prices = [125, 76, 390];
const listItems = items.map((elem, index) => ({ itemName: elem, price: prices[index]}));

listItems;
// [{itemName: "book", price: 125},
// {itemName: "bag", price: 390},
// {itemName: "bag", price: 390}]

## About markDown language:

- https://www.casper.tw/development/2019/11/23/ten-mins-learn-markdown/
- https://markdown.tw/
