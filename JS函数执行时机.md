# 《JS 函数的执行时机》

## 解释为什么如下代码会打印 6 个 6
~~~javascript
let i = 0
for(i = 0; i<6; i++){
  setTimeout(()=>{
    console.log(i)
  },0)
}
~~~
  setTimeout() 就像一个定时器，因此当 i=0 时，它不会马上执行 console.log(i) ，会等 for 循环到不满足 i<6 为止跳出 for 循环，也就是 i=6 ，再执行 console.log(i)；同理执行i=1,i=2,i=3,i=4,i=5，最后显示的就是 6 个 6 。

## 写出让上面代码打印 0、1、2、3、4、5 的方法
1. 方法一
~~~javascript
for(let i=0; i<6; i++){
  setTimeout(()=>{
    console.log(i)
  },0)
}
~~~
2. 方法二
~~~javascript
for(let i=0; i<6; i++){
  console.log(i)
}
~~~

## 除了使用 for let 配合，还有什么其他方法可以打印出" 0、1、2、3、4、5 "?
~~~javascript
let i=0
let interval=setInterval(function(){
    console.log(i)
    i += 1
    if(i===6){
        clearInterval(interval)
    }
},0)
~~~
