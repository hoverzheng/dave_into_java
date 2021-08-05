HashSet



3.要点

* HashSet的底层是使用HashMap来实现的，HashSet的值保存到HashMap的key中，而value都是同一个Object对象，该对象会在构造HashSet对象时创建；
* HashSet 不维护任何顺序，元素将以随机顺序返回；
* HashSet 不允许重复。若在 HashSet 中添加重复元素，则旧值将被覆盖；
* HashSet默认的元素个数和HashMap的容量大小相等，容量默认是：16；负载因子默认是：0.75；
* HashSet不是线程安全的；
* HashSet中允许插入空元素；



3.实战





3.实现原理要点

4.构造函数

当我们调用HashSet() 时，其实是创建了一个HashMap()对象。也就是说HashSet是基于HashMap实现的。

```java
public class HashSet<E>
    extends AbstractSet<E>
    implements Set<E>, Cloneable, java.io.Serializable
{
    static final long serialVersionUID = -5024744406713321676L;
  
  	// 基于HashMap来实现，所以定义一个HashMap成员变量
    private transient HashMap<E,Object> map;

    // 所有的value都设置为PRESENT对象
    private static final Object PRESENT = new Object();

		// 构造函数：初始化容量为16,负载因子为0.75
    public HashSet() {
        map = new HashMap<>();
    }
   ...
}
```







3.小结



