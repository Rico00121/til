When use spring boot, it maps these path to `/` route automatically in default:

```
classpath: /staitc
classpath: /public
classpath: /resources
classpath: /META-INF/resources
```

It means it can access `a.png` under the  `/resources/static/` with `localhost:8080/a.png` 

BUT What we need to pay attention to is that Webflux should explicitly declare the route of accessing static resources.
https://davidecerbo.medium.com/serving-static-resources-with-spring-webflux-and-kotlin-ad831cbd26eb