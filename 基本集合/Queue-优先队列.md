2.优先队列：PriorityQueue

3.PriorityQueue要点

* PriorityQueue是一个队列，其中的元素具有优先级；

* PriorityQueue底层使用数组来保存数据，并按queue[n]的儿子节点为：queue[2n+1]和queue[2(n+1)]的值，从而形成一颗平衡二叉堆的结构；

* PriorityQueue队列中的元素按优先级排序，这样就根据元素的优先级形成了最小（大）堆；
* 元素的优先级是指：元素实现了[`Comparator`](https://docs.oracle.com/javase/8/docs/api/java/util/Comparator.html) 接口，默认是自然顺序进行比较，并按降序对元素进行排列；用户可以定义一个实现了Comparator接口的新类来自定义比较逻辑，在创建队列时，创建该类的对象作为参数。
* PriorityQueue队列是无界的，但插入的元素不能为空，而且必须是可比较的；
* 注意：元素的**迭代遍历**是无序的，不能依赖元素的顺序来使用该队列；但若每次都获取并删除队列的头节点，则是有序的，这一点在有些应用场景中非常有用；
* PriorityQueue的空间增长速度是按50%*oldCapicity的量来增加的，其实现逻辑是，新申请一块大的内存 ，然后把原有数据复制过去；



3.实战

4.基本使用

创建一个元素为字符串的优先队列，PriorityQueue会按照字符的ASCII码来进行排序。当我们每次取出优先队列的头节点时，就是有序的。示例代码如下：

```java
import java.util.PriorityQueue;
import java.util.Queue;

/**
 * 测试优先队列功能的类
 */
class TestPriorityQueue {
    public static void ShowQueueItems(Queue<String> q) {
      	// 每次取队列头部的元素
        while (!q.isEmpty()) {
            String s = q.poll();
            System.out.printf("%s, ", s);
        }
        System.out.println();
    }

  	// 创建一个队列，并向队列中添加字符串成员
    public static void PriorityDemo() {
        Queue<String> cq = new PriorityQueue<>();

        cq.add("name1");
        cq.add("name11");
        cq.add("name22");
        cq.add("helloworld");

        ShowQueueItems(cq);
    }
}

public class SimplePriorityQueue {
    public static void main(String[] args) {
        TestPriorityQueue tpq = new TestPriorityQueue();
        tpq.PriorityDemo();
    }
}
```

以上代码运行输出为：

```
helloworld, name1, name11, name22,
```

可以看到，队列中的元素是有序的，是按字母的ASCII码顺序进行排列的。

4.自定义优先级顺序

```java
import java.util.Comparator;
import java.util.PriorityQueue;
import java.util.Queue;


// 自定义优先级的计算逻辑
class MyComparator implements Comparator<String>
{
    @Override
    public int compare(String x, String y)
    {
        return x.length() - y.length();
    }
}

class TestDIYComparatorPriorityQueue {

    public static void ShowQueueItems(Queue<String> q) {
        while (!q.isEmpty()) {
            String s = q.poll();
            System.out.printf("%s, ", s);
        }
        System.out.println();
    }

    public static void PriorityDemo() {
        Queue<String> cq = new PriorityQueue<>(new MyComparator());

        cq.add("name1");
        cq.add("name11");
        cq.add("name222");
        cq.add("helloworld");

        ShowQueueItems(cq);
    }
}

public class DIYComparatorPriorityQueue {
    public static void main(String[] args) {
        TestDIYComparatorPriorityQueue testpq = new TestDIYComparatorPriorityQueue();
        testpq.PriorityDemo();
    }
}
```

以上代码的输出为：

```
name1, name11, name222, helloworld, 
```

可以看到，输出是按字符串的长度排序的。说明我们自定义的优先级规则生效了。这个优先队列是一个按字符串长度进行排序的最小堆。

3.关键点实现原理分析

4.队列的创建

4.添加元素

4.元素的删除

4.



3.参考文档

