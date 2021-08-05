Map之HashMap



3.Map实现类之间的关系如下图所示

![image-20210803123637502](/Users/hover/work/writemybooks/深入浅出java基础/基本集合/images/map-relation.png)

3.HashMap要点

* HashMap使用一个桶（数组）来保存头节点指针，该头节点指针可能是一个链表的头节点；也可能是一棵红黑树的根节点；所以，可以说HashMap是由，数组、链表、红黑树组成的数据结构。
* 若是key设计的很好的话，HashMap的get和set操作的效率是很快的；key设计的很好的意思是：key的hashCode的值比较分散。
* 允许插入空key和null value。
* HashMap的性能由两个因素影响最大，它们是：初始化容量，和负载因子。初始化容量是指：创建HashMap时桶的位置个数，若太少，可能会导致rehash（增加桶的长度），从而影响性能。负载因子是指：当桶的位置占用到多少时进行rehash，该值默认是0.75；也就是说，默认情况下，当桶的位置的75%被占用时，将会进行rehash操作。
* HashMap可以高效的找到key的值；但当大量key的值相同时，HashMap就变成了一个链表（或一棵树）。
* HashMap不保证遍历的顺序；可以通过`Set<K> keySet()`函数来返回所有的key的对象，但不保证其顺序。

3.HashMap实战

4.基本使用

```java
import java.util.HashMap;
import java.util.Iterator;
import java.util.Map;

public class UseHashMap {
    // 定义一个Map对象的数据结构
    Map<Integer, String> hmap;

    public UseHashMap() {
        hmap = new HashMap<>(128);
    }

    // 放入几个元素到HashMap中
    public void putItems() {
        hmap.put(12, "Chaitanya");
        hmap.put(2, "Rahul");
        hmap.put(7, "Singh");
        hmap.put(49, "Ajeet");
        hmap.put(3, "Anuj");
        hmap.put(1, "hello world");
    }

  	/** ------------遍历元素的操作------------------**/
    // 通过获取所有的key对象来遍历HashMap
    public void TravelMap() {
        System.out.println("通过key来遍历HashMap：");
        for (Integer k: hmap.keySet()) {
            System.out.printf("%d: %s, ", k, hmap.get(k));
        }
        System.out.println("");
    }

    // 通过迭代器来遍历元素
    public void TravelMapByIter() {
        System.out.println("通过迭代器来遍历HashMap：");
        Iterator iterator = hmap.entrySet().iterator();
        while (iterator.hasNext()) {
            Map.Entry me2 = (Map.Entry) iterator.next();
            System.out.printf("%d: %s, ", me2.getKey(),me2.getValue());
        }
        System.out.println("");
    }

    // 通过返回key-value对来遍历HashMap
    public void TravelMapByEntrySet() {
        System.out.println("通过返回key-value对，来遍历HashMap：");
        for (Map.Entry me: hmap.entrySet()) {
            System.out.printf("%d: %s, ", me.getKey(),me.getValue());
        }
    }

    public static void main(String[] args) {
        UseHashMap uhp = new UseHashMap();
        uhp.putItems();
        uhp.TravelMap();
        uhp.TravelMapByIter();
        uhp.TravelMapByEntrySet();
    }
}
```

以上代码的输出如下：

```
通过key来遍历HashMap：
1: hello world, 2: Rahul, 3: Anuj, 7: Singh, 12: Chaitanya, 49: Ajeet, 
通过迭代器来遍历HashMap：
1: hello world, 2: Rahul, 3: Anuj, 7: Singh, 12: Chaitanya, 49: Ajeet, 
通过返回key-value对，来遍历HashMap：
1: hello world, 2: Rahul, 3: Anuj, 7: Singh, 12: Chaitanya, 49: Ajeet, 
```

虽然输出的key-value是有顺序的，但实际的顺序是不确定的，所以不能依赖该顺序来进行软件的开发。



3.HashMap的实现原理





3.参考文献





