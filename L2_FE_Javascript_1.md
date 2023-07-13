# Javascript

##  Week 1 Introduction

### 1. Data types
Number, String, Boolean,  
Null, Undefined,  
BigInt, Symbol.

### 2. Operator
運算子

#### Arithmetic Operators
算術運算符
![](https://hackmd.io/_uploads/rkYVkKtKn.png)

#### Comparison Operators
比較運算符
![](https://hackmd.io/_uploads/rkrdkttF2.png)

#### Logical Operators
邏輯運算符
![](https://hackmd.io/_uploads/rJZbxYYYn.png)

### 3. Conditional Statements
條件語句

#### if / else if / else
適合不超過三種狀況需要選擇

#### switch
適合超過三種況狀以上

### 4. Loop
循環

#### for
set the value;  
specify the condition;  
increment the counter.

#### while
start outside;  
increment inside;  

#### Nested Loop
嵌套循環
常用於sorting

## Week 2 Building Blocks 建立模塊(?

### 1. Function

function name(parameters){
    
};

name(argument);

### 2. Object
with key value pair
```javascript!
let obj = 
{
    key1:"value1",
    key2:"value2"
};
```
> **Arrays are Objects**
> **Strings are Arrays**

### 3. Arrays methods

1. push()
增加至陣列最後一個item
```javascript!
let fruits = [];
fruits.push("apple"); // ['apple']
```

2. pop()
移除陣列最後一個item
```javascript!
fruits.pop();
console.log(fruits); // []
```

### 4. Math object

#### 常數

1. Math.PI
> 3.14159

2. Math.E
> 2.718

3.  Math.LN2
> 0.693

#### 圓

1. Math.ceil()
無條件進位

2. Math.floor()
無條件捨去

3. Math.round()
四捨五入

4. Math.trunc()
取整數

### 5. Strings Methods

1. concat()
連接字串
```javascript!
"Wo".concat("rl").concat("d"); // 'World'
```

2. indexof()
返回這個字母所在的位置(從前面數來的第一個)]
```javascript!
"ho-ho-ho".indexOf('h'); // 0
"ho-ho-ho".indexOf('o'); // 1
"ho-ho-ho".indexOf('-'); // 2
```
> lastIndexOf() -> 從後面數來第一個

3. split()
從()中的地方切開字串，返回一個array
```javascript!
"ho-ho-ho".split("-"); // ['ho', 'ho', 'ho']
```

4. 變換大小寫
```javascript!
greet.toUpperCase(); // "HELLO, "
greet.toLowerCase(); // "hello, "
```

### 6. 自定義物件方法
```javascript!
//example of adding properties and methods to an object
var car = {};
car.mileage = 98765;
car.color = "red";
console.log(car);
car.turnTheKey = function() {
    console.log("The engine is running")
}
car.lightsOn = function() {
    console.log("The lights are on.")
}
console.log(car);
car.turnTheKey();
car.lightsOn()
```
> { mileage: 98765, color: 'red' }
> 
> {
>   mileage: 98765,
>   color: 'red',
>   turnTheKey: [Function (anonymous)],
>  lightsOn: [Function (anonymous)]
> }
> 
> The engine is running
> 
> The lights are on.

### 7. bugs & errors  

#### **1. Error Types**
1. **SyntaxError**  
語法錯誤：使用javascript不存在的語法時發生  
ex.`let a "a" // Uncaught SyntaxError: Unexpected string`
2. **TypeError**  
類型錯誤：在一些類型上使用不支持的方法時發生  
ex. `"hello".pop() // Uncaught TypeError: "hello".pop is not a function`
3. **ReferenceError**  
引用錯誤：使用的未宣告的變量時發生  
ex. `console.log(username); // Uncaught ReferenceError: username is not defined`
5. **RangeError**  
範圍錯誤：向函數提供一些超過可接受範圍數據的時候發生  
ex. `(10).toString(100); // Uncaught RangeError: toString() radix argument must be between 2 and 36`

`throw new ReferenceError();`
可以用來測試引用錯誤的結果

#### 2. Types of empty values
1. Null  
3. Undefined  
3. Empty strings  

#### 3. Error Handling
```javascript!
function addTwoNums(a,b) {
    try {
        if(typeof(a) != 'number') {
            throw new ReferenceError('the first argument is not a number')
        } else if (typeof(b) != 'number') {
            throw new ReferenceError('the second argument is not a number')
        } else {
            console.log(a + b)
        }
    } catch(err) {
        console.log("Error!", err)
    }
}
addTwoNums(5, "5")
console.log("It still works")
```
> 1. try catch 用法
> 2. try 裡面加入if判斷
> 3. 當a,b非number時，丟出ReferenceError
> 4. 在呼叫addTwoNums時，就算出現錯誤，後續的程式也會繼續運作。

>Error! ReferenceError: the second argument is not a number
>
>**It still works**

### 8. Defensive Programming

source code:
```javascript!
function letterFinder(word, match) {
    for(i = 0; i < word.length; i++) {
        if(word[i] == match) {
            //if the current character at position i in the word is equal to the match
            console.log('Found the', match, 'at', i)
        } else {
            console.log('---No match found at', i)
        }
    }
}
```

defensive programming:
```javascript!
function letterFinder(word, match) {
    var condition1 = typeof(word) == 'string' && word.length >= 2;  
    //if the word is a string and the length is greater than or equal to 2
    var condition2 = typeof(match) == 'string' && match.length == 1; 
    //if the match is a string and the length is equal to 1
    if(condition1 && condition2) { //if both condition matches
        for(var i = 0; i < word.length; i++) {
            if(word[i] == match) {
                //check if the character at this i position in the word is equal to the match
                console.log('Found the', match, 'at', i)
            } else {
                console.log('---No match found at', i)
            }
        }
    } else {
        //if the requirements don't match
        console.log("Please pass correct arguments to the function")
    }
}
letterFinder([],[])
letterFinder("cat","c")
```
> 1. 宣告condition
> 2. 將狀況條件包裹在for外面，假如條件都達到，執行for迴圈。
> 3. 寫下條件未達成時console.log

## Week 3 Programming Paradigms 程式範例
FP & OOP

### 1. functional programming
concepts and ideas：
#### **1. First-class functions**
一級函式
> * 可以傳遞給其他函式
> * 貯存在變數內部
> * 透過其他函式返回  

範例：
```javascript!
function addTwoNums(a, b) {
    console.log(a + b)
}

function randomNum() {
    return Math.floor((Math.random() * 10) + 1);
}
function specificNum() { return 42 };

var useRandom = true;

var getNumber;

if(useRandom) {
    getNumber = randomNum
} else {
    getNumber = specificNum
}

addTwoNums(getNumber(), getNumber())
```
> addTwoNums()為主要啟動的函式
> randomNum()返回1-10的隨機數字
> SpecificNum()返回一特定數字42
> 變量useRandom = true
> 接著用判斷式來判斷隨機返回的數字，
> 但因為useRandom = true，因此getNumber返回的數字為隨機數字，反之為特定數字

#### **2. Higher-order functions**
高階函式  
> * 接受其他函式做為參數(arguments)
> * 當呼叫時返回其他函數  

範例：延續上一個例子
```javascript!
function addTwoNums(getNumber1, getNumber2) {
    console.log(getNumber1() + getNumber2());
}
```
> 這裡重新定義了addTwoNums()
> 將a與b改成getNmber1,getNumber2
> 並且console.log呼叫getNumber1()

此時呼叫addTwoNums函數時：
```javascript!
addTwoNums(specificNum, specificNum); // returned number is 84
addTwoNums(specificNum, randomNum); // returned number is 42 + some random number
```
> 高階函數可以很靈活的運用

#### **3. Pure Functions and side-effects**
純函數以及副作用

1. Pure Function
一樣的argument總是返回一樣的結果
```javascript!
function addTwoNums(a, b) {
    console.log(a + b)
}
addTwoNums(5,6); // 11
```

2. Side-Effects
當執行函式時會改變外在的變數
包含：
* 改變函式外在的變數，或是依賴外在的變數
* 呼叫瀏覽器的API(包含console)
* 呼叫Math.random()，這讓每次的結果很難重複

### 2. Scope

Block Scope from ES6
let / const
```javascript!
let color = "red";
// global scope

if (color == "red")
{
    let color == "blue";
}
// Block scope Curly Braces

console.log(color);
// 'red'
```

### 3. object oriented programming

#### 1. Classes

```javascript!
class Car {
    constructor(color, speed) {
        this.color = color;
        this.speed = speed;
    }
    
    turboOn() {
        console.log("turno is on!")
    }
}
```
> * 使用class來宣告建構式方程式(Constructor)  
> * Methods寫在constructor之外

```javascript!
const car1 = new Car("red", 120)

car1.turboOn();
// "turno is on!"
```
> * 使用new建立instance，同時呼叫Car並將參數傳入class內部的constructor  
> * car1能夠使用方法turboOn()

#### 2. OOP介紹

1. 可以將code模組化(modularized)
2. 使code更有彈性
3. 使code可以重複使用

所有的物件都屬於Object class，也就是他們都能夠使用繼承於Object的方法，  
例如生成instance的方法Object.create()

```javascript!
class Animal { /* ...class code here... */ }

var myDog = Object.create(Animal)

console.log (Animal)
```
> 但通常我們會用class以及keyword new


##### 基本原則

1. inheritance(繼承)
2. encapsulation(封裝)
3. abstraction(抽象)
4. polymorphism(多態性)
---

##### **1. Inheritance(繼承)**
有一個base class，並往下衍伸，比方說  
"鳥類"屬於"動物"的一個class  
"老鷹"屬於"鳥類"的一個class  
在code之中，就可以用關鍵字extends來建構這樣的繼承鍊
```javascript!
class Animal { /* ...class code here... */ }
class Bird extends Animal { /* ...class code here... */ }
class Eagle extends Bird { /* ...class code here... */ }
```

##### **2. Encapsulation(封裝)**
即使不知道這個方法的code也能使用，例如：
```javascript!
"abc".toUpperCase();
```
> 雖然我不清楚toUpperCase()這個方法是啥，但我會用

##### **3. Abstraction(抽象)**
與封裝很像，但概念不同，簡言之，  
Abstraction是提取將要做的事情的概念，而非步驟。

##### **4. Polymorphism(多態性)**
根據不同的情況，同一種方法可以使結果不同

* 案例1.
```javascript!
const bicycle = {
    bell: function() {
        return "Ring, ring! Watch out, please!"
    }
}
const door = {
    bell: function() {
        return "Ring, ring! Come here, please!"
    }
}

bicycle.bell(); // "Get away, please"
door.bell(); // "Come here, please"
```
> 宣告兩個物件，一個是腳踏車，一個是門  
> 他們有著同樣的方法：bell，但用途卻不同

```javascript!
function ringTheBell(thing) {
    console.log(thing.bell())
}

ringTheBell(bicycle); // Ring, ring! Watch out, please!
ringTheBell(door); // "Ring, ring! Come here, please!"
```
> 接著，宣告一個函式ringTheBell()，接收一個參數thing(object)  
> 呼叫這個函式時，他會使用參數所擁有的方法bell。  
> 這裡可以得知，同樣的函式，透過不同的參數也能獲得不同的結果。

* 案例2.
```javascript!
"abc".concat("def"); // 'abcdef'
"abc" + "def" // 'abcdef'

["abc"].concat(["def"]); // ['abc', 'def']
["abc"] + ["def"]; // ["abcdef"]
```
> concat()連接兩個字串時功能跟"+"一樣。  
> 但如果連接兩個array時，就與"+"得到的結果不相同。  
> 這也代表著concat這個方法在面對不同的型別有著Polymorphic behavior。

#### 3. Constructors 建構函式
javascript之中有許多內建的物件  

包含`Math`, `Date`, `Object`, `Function`, `Boolean`, `Symbol`, `Array`, `Map`, `Set`, `Promise`, `JSON`  
這些通常稱為"native objects"。

Constructor functions則是一種特殊的函式，使用的方法需要先用運算子`new`。  
