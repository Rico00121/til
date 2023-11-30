# `let()` and `run()`
## Same
return the last called result of context object.

## Difference
`let()` make context object `it` as lambda parameter, it means access it outside. Use it if you want to simply chain call.

`run()` get the context object `this` pointer in our scope block { }, it means we access it like inside (`T.run(block: () => {}`, acctually it is pass the T's pointer to block, so you can not ). Use it if you want to it run something


# `also()` and `apply()`
## Same
return the context object rather than result in lambda block.

## Difference
`also()` make context object `it` as lambda parameter. It is a side-effect function, it means what it do will not affect context object itself, it just do something by the way~

`apply()` get the context object `this` pointer in our scope block { }, it do something about itselt and return itself.


# `with()`
Get this pointer scope, just for simplifying code when you are going to access many inside fields.

```kotlin
with(item) {
            name = request.name
            masterName = request.masterName
            contactName = request.contactName
            contactTel = request.contactTel
            email = request.email
            application = request.application
            address = request.address
            puThickness = request.puThickness
            size = request.size
        }
``` 
 
