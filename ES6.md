# ES6
### defineProperty
- 属性描述符 
writable
enurmable
configurable
value
get
set

1.测试writable,是否可写
```
    obj={a:1}
    Object.defineProperty(obj,"a",{
        writable:false
    })
```
2.测试configurable,是否可被删除
```
    obj={a:1}
    Object.defineProperty(obj,"a",{
        configurable:false
    })
```
3.测试value
```
    obj={a:1}
    Object.defineProperty(obj,"a",{
        value:false
    })
```
4.测试enurmable,是否被枚举
```
    obj={a:1}
    Object.defineProperty(obj,"a",{
        enurmable:false
    })
```
5.测试get/set,
```
    obj={a:1}
    Object.defineProperty(obj,"a",{
        get(){
            return 'abc'
        },
        set(val){
            console.log('val...',val)
        }
    })
```
---
### proxy
```
    var obj2={};
    var proxy=new Proxy(obj2,{
        get(target,key){
            console.log(target,key)
        },
        set(target,key,val){
            console.log(target,key,val)
        }
    })
```
---
### Promise,asunc/await,generator
1.Promise的三种状态：pennding,resolved/fulfilled,rejected
- pending：初始值，不是fulfilled，也不是rejected
- fulfilled：代表操作成功
- rejected：代表操作失败

2.Promise的特性：控制时序，封装复用，立即执行

3.Promise的两个静态方法：resolve,reject


```
    function loadImg(src){
        return new Promise((resolve,reject)=>{
            let img=new Image();
            img.src=src
            img.onload=function(){
                resolve(img)
            }
            img.onerror=function(e){
                reject(e)
            }
        })
    }
    let url="http://img.mp.itc.cn/upload/20170220/3bde98f642f546be95b2d242994897aa_th.jpg"
    loadImg(url).then(res=>{
        document.body.appendChild(res)
        return res
    },err=>{
        console.log(err)
    }).catch(()=>{
        
    }).finally(()=>{
        
    })
```
resolve函数的作用：在异步操作成功时调用，并将异步操作的结果，作为参数传递出去； 

reject函数的作用：在异步操作失败时调用，并将异步操作报出的错误，作为参数传递出去。

then方法会返回一个Promise。它有两个参数，分别为Promise从pending变为fulfilled和rejected时的回调函数（第二个参数非必选）。这两个函数都接受Promise对象传出的值作为参数。

