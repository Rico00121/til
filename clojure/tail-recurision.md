# Mutal recursion
```javascript
function funcA(x) {
    return funcB(x)
}

function funcB(x) {
    return funcA(x)
}

funcA(funcB(1));
```
It will over stack.

# Non-tail recursion
Factorial:
```javascript
function fact(n){
    if(n==0)return 1;
    return n*fact(n-1);
}
```
The last operation is mutiplication rather than calling itself.

# Tail recursion
```javascript
function fact(n, acc){
    if(n==0)return acc;
    return fact(n-1, acc*n)
}
```
It very like `for` loop:
```javascript
function fact(n){
    var acc=1,i=n
    while(i!=0){
        acc=acc*i;
        i-=1;
    }
    return acc
}
```
In clojure, we use `recur` to make sure tail recursion.

# Trampoline
`(trampoline f)(trampoline f & args)`
trampoline can be used to convert algorithms requiring mutual
recursion without stack consumption. 

Calls f with supplied args, if
any. If f returns a fn, calls that fn with no arguments, and
continues to repeat, until the return value is not a fn, then
returns that non-fn value. 



