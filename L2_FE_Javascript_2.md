# Javascript

[![hackmd-github-sync-badge](https://hackmd.io/u9r3UzBwRgisHYO_LGWIpw/badge)](https://hackmd.io/u9r3UzBwRgisHYO_LGWIpw)


## Week 3 Programming Paradigms 程式範例(續)

### 1. for of loop

```javascript!
const car = {
    speed: 100,
    color: "blue"
}

for(prop of car) {
    console.log(prop)
}

//  Uncaught TypeError: car is not iterable
``` 
> 物件是不可以迭代的。

```javascript!
const colors = ['red','orange','yellow']
for (var color of colors) {
    console.log(color);
}

// red
// orange
// yellow
```
> 陣列可以

#### Object內建方法
複習一下

1. Object.keys()
```javascript!
const car2 = {
    speed: 200,
    color: "red"
}
console.log(Object.keys(car2)); // ['speed','color']
```
> 抓出object的key值，return為一陣列。

2. Object.values()
```javascript!
const car3 = {
    speed: 300,
    color: "yellow"
}
console.log(Object.values(car3)); // [300, 'yellow']
```
> 抓出object的value值，return為一陣列。

3. Object.entries()
```javascript!
const car4 = {
    speed: 400,
    color: 'magenta'
}
console.log(Object.entries(car4));

// [ ['speed', 400], ['color', 'magenta'] ]
```
> 將object中的key,value抓出，return排列為一個二維的陣列

```javascript!
var clothingItem = {
    price: 50,
    color: 'beige',
    material: 'cotton',
    season: 'autumn'
}

for( key of Object.keys(clothingItem) ) {
    console.log(clothingItem[key])
}

// 50
// 'beige'
// 'cotton'
// 'autumn'
```
> for of 搭配 Object.keys() 就可以解構出物件中的 value

### 2. template literals 模板語法
```javascript!
let greet = "Hello";
let place = "World";
console.log(`${greet} ${place} !`) 

// Hello World !

console.log(`${1 + 1 + 1 + 1 + 1} stars!`) 

// 5 stars!
```

### 3. Working with arrays

1. forEach
```javascript!
const fruits = ['kiwi','mango','apple','pear'];

function appendIndex(fruit, index) {
    console.log(`${index}. ${fruit}`)
}
fruits.forEach(appendIndex);

//0. kiwi
//1. mango
//2. apple
//3. pear
```

2. filter()
```javascript!
const nums = [0,10,20,30,40,50];

nums.filter( function(num) {
    return num > 20;
})

//[30,40,50]
```
> 接受filter條件下返回的值，並形成新的array

3. map
```javascript!
const nums2 = [0,10,20,30,40,50];

nums2.map( function(num) {
    return num / 10
})

//[0,1,2,3,4,5]
```
> 逐一將值取出，經過條件後形成新的array

### 4. `Map` constructor

map類似於object，但他的instance沒有繼承，沒有prototype
```javascript!
let bestBoxers = new Map();
bestBoxers.set(1, "The Champion");
bestBoxers.set(2, "The Runner-up");
bestBoxers.set(3, "The third place");

console.log(bestBoxers);

// Map(3) {1 => 'The Champion', 2 => 'The Runner-up', 3 => 'The third place'}
```

獲取value可以用get方法
```javascript!
bestBoxers.get(1); // 'The Champion'
```

### 5. `Set` constructor
可以用再array上，同時就可以用來快速的篩選調相同的值
```javascript!
const repetitiveFruits = ['apple','pear','apple','pear','plum', 'apple'];
const uniqueFruits = new Set(repetitiveFruits);
console.log(uniqueFruits);

// Set(3) {'apple', 'pear', 'plum'}
```
> 返回的結果是一個key=value的物件

### 6. spread operator & rest operator 展開運算符 & 其餘運算符

1. rest operator
```javascript!
const fruits = ['apple', 'pear', 'plum']
const berries = ['blueberry', 'strawberry']

const fruitsAndBerries = [...fruits, ...berries] // concatenate

console.log(fruitsAndBerries); 

// ['apple', 'pear', 'plum', 'blueberry', 'strawberry']
```
> 同樣的方法也適用於object

2. spread operator

將字串展開
```javascript!
const greeting = "Hello";
const arrayOfChars = [...greeting];

console.log(arrayOfChars); 
//  ['H', 'e', 'l', 'l', 'o']
```

3. copy array
```javascript!
const fruits1 = ['apples', 'pears']
const fruits2 = [...fruits1]
https://hackmd.io/u9r3UzBwRgisHYO_LGWIpw#
console.log(fruits1, fruits2)
// ['apples','pears'] ['apples','pears']
```

### 7. testing

1. Jest introduce

在javascript中
```javascript!
function concatStrings(a,b){
    return a + b;
}

concatStrings("123","456")
//  123456
```
> 預期結果為123456

使用JEST來測試
```javascript!
expect(concatStrings("123","456")).tobe("123456");
```

2. Refactoring 重構  
在不影響結果的情況下，重新設計程式

3. End-to-end(e2e) testing  
透過使用者與介面互動，來測試整個預期的功能  
特點：最耗時耗費資源  
常用軟體：WebdriverJS, Protractor, Cypress

4. integration testing 集成測試  
測試各個部分如何協同工作  
特點：較少的時間
常用軟體:React testing library, Enzyme

5. unit testing 單元測試  
測試每個具備獨立功能的片段，例如function
特點：最快且最容易編寫

### 8. Jest 
`npm install --save-dev jest`
```javascript!
{ //...
    "script":{
        "test": "jest";
    },
}
```
`npm run test`

todo.test.js
```javascript!
test("return true if statusOfKeys exists", function({
    expect(statusOfKeys).toboDefined()
})

function statusOfKeys(){}
```

1. code coverage  
代碼覆蓋率，在測試上，覆蓋率越高可能抓到bug的機率越低

2. mocking  
在測試時將互相依賴的單元分開來，這有助於unit testing

3. Snapshot testing  
用來確認DOM操作沒有重新改變至原始的程式代碼

4. TDD  
test-driven development  
測試驅動開發  

傳統開發：取得需求->開發->測試  
TDD：取得需求->撰寫failing test->開發通過測試->程式優化  

原則：越少code越好