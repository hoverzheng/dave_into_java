Map-TreeMap



3.TreeMap的要点

* 以红黑树的数据结构来保存元素，所以TreeMap中的元素是排好序的；
* TreeMap的key遍历是有序的，而且很高效；
* key的排序可以使用Comparable接口或Comparator接口来排序；
* TreeMap中的key是按key的值升序排列的；



3.TreeMap实战

实战的代码分为两个部分，一个是基本操作；一个是创建一个逆序的TreeMap。

```java
import java.util.*;

public class DoTreeMap {
    // TreeMap的基本操作
    public static void BaseTreeMap() {
        Map<String, Integer> tmap = new TreeMap<>();

        tmap.put("aa", 1);
        tmap.put("bb", 2);
        tmap.put("cc", 3);
        tmap.put("dd", 4);
        tmap.put("cc", 5);
        tmap.put("ee", 6);

        // 遍历treemap
        Set set = tmap.entrySet();
        Iterator iterator = set.iterator();
        while (iterator.hasNext()) {
            Map.Entry me = (Map.Entry)iterator.next();
            System.out.printf("%s: %d, ", me.getKey(), me.getValue());
        }
        System.out.println("");

        // 通过key遍历TreeMap
        for (String k: tmap.keySet()) {
            System.out.printf("%s: %d, ", k, tmap.get(k));
        }
        System.out.println("");

        // 查看包括某个值的节点
        boolean isVExist = tmap.containsValue(5);
        System.out.printf("value %d is %s.\n", 5, Boolean.toString(isVExist));
    }

    // 逆序打印元素的值
    public static void reverseTreeMap() {
        Map<String, Integer> tmap2 = new TreeMap<>(Collections.reverseOrder());

        tmap2.put("aa", 1);
        tmap2.put("bb", 2);
        tmap2.put("cc", 3);
        tmap2.put("dd", 4);
        tmap2.put("cc", 5);
        tmap2.put("ee", 6);

        // 通过key遍历TreeMap
        System.out.println("逆序遍历key的值： ");
        for (String k: tmap2.keySet()) {
            System.out.printf("%s: %d, ", k, tmap2.get(k));
        }
        System.out.println("");

    }

    public static void main(String[] argss) {
        BaseTreeMap();
        reverseTreeMap();
    }
}
```



3.TreeMap实现原理





3.小结



