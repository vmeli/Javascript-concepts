# Execution Context and Lexical Environments

# Idea
What happen with your code? 

## Syntax Parser
Is a program that reads your code and determines what it does and if its grammar is valid.

- Compilers
- Interpreters

Code:

function sayHi(){
	var hi = 'Hi!!';
}

Computer Instructions:

Function
	Variable


Further reading:
 - https://www.quora.com/How-does-parsing-work
 - https://softwareengineering.stackexchange.com/questions/138521/is-javascript-interpreted-by-design
 - https://www.quora.com/What-is-the-difference-between-a-compiler-and-an-interpreter/answers/7670223


## Lexical Environments
 Where it's written and what surrounds it.

 Further reading:
 http://es5.github.io/#x10.2


## Execution Context

A Wrapper to help manage the code that is running.

Hoisting: 

/* First Scenario */
var a = 'Hello Lab';

function b(){
	console.log('called');
}

b();
console.log(a);

/* Second Scenario */

b();
console.log(a);

var a = 'Hello Lab';

function b(){
	console.log('called');
}


/* Third Scenario */

b();
console.log(a);

function b(){
	console.log('called');
}


Hosting Definition:

Setup Memory Space for variables and functions before your code begins to be executed line by line.

** All variables in Javascript are initially set to undefined.

Life Cycle:
- Creation: ( Parse is running and recognize where you've created variables and where you've created functions ).
    - Variables, functions is created ( Global Object is created )
    - "this" is determined
    - Outer Environment
    - Hoisting
- Execution ( line by line )
	- Code is interpreted
	- Executed

Let's understand with an example:
  function sayHi( name ){
   	var hi = 'Hello my friend!';
   	var say = function(){
   		alert( hi );
   	};
   	function foo(){};
  }
  sayHi('Jp');

Let's create execution contex for this example:

ecSayHi(){
	variableObject : {
		arguments: {
           0: 'Jp',
           length: 1
	    },
	    name: 'Jp',
	    f : a pointer memory to "f" function
	    hi : undefined,
	    say: undefined
    },

   scopeChain : {},
   thisForSayHi : {}
}

**The call stack is a collection of execution context.

## undefined

Scenario 1: 

var myVar;
console.log( myVar );

Scenario 2:

console.log( myVar2 );

Undefined is the same as Not defined? --- No.

Internally Undefined means: The variable hasn't been set. Is a special keyword/value.

Scenario 1 : 

var a;
console.log(a);

if ( a === undefined ){
	console.log('a is undefined' );
}else{
	console.log('a is defined');
}

Scenario 2: 

console.log(a);

if ( a === undefined ){
	console.log('a is undefined' );
}else{
	console.log('a is defined');
}

Never do this:
var a = undefined;


Scenario:
var a;
console.log(a);

if ( a === undefined ){
	console.log('a is undefined' );
}else{
	console.log('a is defined');
}


Is difficult to debug, althought you don't know if is undefined because your set it or because JS engine set it.


## Execution Phase detail


function b(){
	console.log('called b');
}

b();
console.log(a);
var a = 'Hello Lab';
console.log(a);


Further reading
https://dzone.com/articles/javascript-execution-context
