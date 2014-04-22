String
-


方法名 | 参数 | 返回值 | 示例
------------ | ------------- | ------------ | -----------------
codePointAt | 字符在字符串中的位置  | 字符的unicode码，整形| text.codePointAt(0) 
fromCodePoint | unicode码 |对应字符|String.fromCodePoint(134071)
normalize|"NFC" (default), "NFD", "NFKC", or "NFKD"||
contains()|字符串/开始搜索的位置|boolean|msg.containsWith("o", 4)
startsWith|字符串/开始搜索的位置|boolean|msg.startsWith("o", 4)
endsWith|字符串/开始搜索的位置|boolean|msg.endsWith("o", 4)
repeat|整形，指定字符串重复的次数|重复后的新字符串|"x".repeat(3)

Numbers
-
方法名 | 参数 | 返回值 | 示例
------------ | ------------- | ------------ | -----------------
parseInt |   | | 
isFinite |||
isNaN |||
parseFloat|||
isInteger|||

Math
-

方法名 | 参数 | 返回值 | 示例
------------ | ------------- | ------------ | -----------------
Math.pow |   | | 
Math.acosh|||
Math.asinh|||
Math.atanh|||
Math.cbrt|||
Math.clz32|||
Math.cosh|||
Math.expm1|||
Math.fround|||
Math.hypot|||
Math.imul|||
Math.log1p|||
Math.log10|||
Math.log2|||
Math.sign|||
Math.tanh|||
Math.trunc|||



Object
-

方法名 | 参数 | 返回值 | 示例
------------ | ------------- | ------------ | -----------------
Object.is |   | | 

	console.log(+0 == -0);              // true
	console.log(+0 === -0);             // true
	console.log(Object.is(+0, -0));     // false
	
	console.log(NaN == NaN);            // false
	console.log(NaN === NaN);           // false
	console.log(Object.is(NaN, NaN));   // true
	
	console.log(5 == 5);                // true
	console.log(5 == "5");              // true
	console.log(5 === 5);               // true
	console.log(5 === "5");             // false
	console.log(Object.is(5, 5));       // true
	console.log(Object.is(5, "5"));     // false
	
块级作用域
-

##### let

	function getValue(condition) {
	
	    if (condition) {
	        let value = "blue";
	
	        // other code
	
	        return value;
	    } else {
	
	        return null;
	    }
	}
	
#### const
> const是块级作用域，声明过的不能再声明

	var message = "Hello!";
	let age = 25;
	
	// Each of these would cause an error given the previous declarations
	const message = "Goodbye!";
	const age = 30;

函数
-

##### Default Parameters

	function combineText(start, middle = "", end = "") {
	    return start + middle + end;
	}

##### Rest Parameters
	function sum(first, ...numbers) {
	    let result = first,
	        i = 0,
	        len = numbers.length;
	
	    while (i < len) {
	        result += numbers[i];
	        i++;
	    }
	
	    return result;
	}
##### Arrow Functions

##### Still Functions

