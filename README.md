# BFIR (Brainfuck Intermediate Representation)
BFIR is a web based transpiler that is similar to an ASM and designed to be used for easily designing Brainfuck Applications.

## How To Use?
Every line is a new command. Spaces seperate each operation, to write spaces within strings you use "\_", to use "\_" normally you should write "\\" before it, and "\\\\" if you want to write "\\" without effecting anything.

How do you execute BFIR?
Firstly, put this in the html header with the BFIR.js file in your project:
```html
<script src="BFIR.js"></script>
```
Now you just put a script element in the body. You can either compile it to raw brainfuck or execute the brainfuck as an unoptimized js function.
```javascript
//Get Raw Compiled Code
var bf = compileBFIR("# Code Here");

//Unoptimized Js Function
var fn = execBFIR("# Code Here",(text,num)=>{
  //Output Function (Takes text and number version of cell byte)
});

//The string is taken as input, split from start to end whenever "," is used
fn("Input String");
```

The programming language uses a stack to pass arguments into most API functions. The base operations or keywords are as follows:
### Base Operations
- \# [Comment]
- inline [brainfuck code]
- exec [API function]
- malloc [name] (size: default 1)
- push# [number]
- push$ [string]
- pushRef [variable name] (index)
- sliceRef [slice start] [slice end]
- CLEAR
- clearRef [variable] [index]
- move [variable a] [index] [variable b] [index]
- moveAdd \<same as move>
- moveSub \<same as move>
- copy \<same as move>
- copyAdd \<same as move>
- copySub \<same as move>
- inc [variable name] (index)
- dec [variable name] (index)
- while [variable name] (index)
- repeat [variable name] (index)
- next [variable name] (index)

Here is a list of API functions included when compiling BFIR. This includes, after the function name, the arguments taken from the stack in order from First to Last.
### API Functions
- clone [reference a] [reference b]
- sendRaw [string]
- sendRef [reference]
- read [reference]
- setString [reference] [string]
- addString [reference] [string]
- subString [reference] [string]
- setNum [reference] [number]
- addNum [reference] [number]
- subNum [reference] [number]
