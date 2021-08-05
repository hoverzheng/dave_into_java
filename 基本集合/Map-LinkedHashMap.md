LinkedHashMap的使用



3.基本使用

* 会维护一个节点插入的顺序，保证遍历时按插入顺序进行遍历；
* 注意：当一个key-value已经存在，再次插入key时，该key的遍历顺序不受影响；
* 



3.实战

4.基本使用





4.开启accessOrder选项

​	在创建LinkedHashMap时，当开启accessOrder选项，LinkedHashMap中的元素会按LRU（最少最近访问）访问来进行组织。也就是说，会把get（访问）过的元素添加到链表的尾部。这样，就可以保证最少访问过的元素在链表的头部。

通过开启该选项，我们就可以完成一个LRU队列。

```java
public class DoLinkedHashMap {
    public static void TravelMap(Map<String, Integer> lmap) {
        lmap.forEach(
                (k,v) -> {
                    System.out.printf("%s: %d, ", k, v);
                }
        );
        System.out.println("\n---");
    }

    public static void main(String[] args) {
        Map<String, Integer> lhmap = new LinkedHashMap<>(128, 0.75f, true);

        lhmap.put("aa1", 1);
        lhmap.put("bb1", 2);
        lhmap.put("cc1", 3);
        lhmap.put("dd1", 4);
        
        lhmap.get("cc1");
        lhmap.get("aa1");
        
        TravelMap(lhmap);
    }
}
```

可以猜一下元素的输出顺序是什么？实际的输出如下：

```
bb1: 2, dd1: 4, cc1: 3, aa1: 1, 
```

原因是，我们开启了accessOrder选项，当添加节点完成后，我们get了cc1和aa1两个元素，这样cc1和aa1这两个元素就先后被添加到了链表的尾部，从而在遍历时这两个元素的顺序放到了最后。



4.设计一个LRU系统

可以通过重载LinkedHashMap的removeEldestEntry函数来实现。

如果此映射应删除其最旧的条目，则返回 true。在将新条目插入地图后，put 和 putAll 会调用此方法。它为实现者提供了每次添加新条目时删除最旧条目的机会。如果映射代表缓存，这很有用：它允许映射通过删除陈旧条目来减少内存消耗。

//  todo: ？？？

```java
class LRUCacheDemo extends LinkedHashMap<String, Object>{
	private static final long serialVersionUID = -1838771409260368496L;
	private int maxCapacity;
	
	public LruCache(int maxCapacity) {
		super(maxCapacity, 0.75f, true);
		this.maxCapacity=maxCapacity;
	}
	
	/**
	 * 方法的返回值决定了容器在满的时是否移除元素.
	 * true:表示要移除
	 * false:表示不移除
	 */
	@Override
	protected boolean removeEldestEntry(java.util.Map.Entry<String, Object> eldest) {
		return size()>maxCapacity;
	}
}
```





3.实现原理



3.小结

