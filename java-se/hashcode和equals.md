# hashcode和equals

1. equals 

> 

2. hashcode

> HashSet检查重复时会先调用hashcode()判断对象加入的位置(hash冲突)，后调用equals查看是否值相同

3. 总结

> 两个对象相等，则hashcode一定也是相同的  
> 两个对象hashcode相等，双方equals不一定为true
> 两个对象相等，那么双方equals一定为true