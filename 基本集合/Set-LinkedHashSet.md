LinkedHashSet



3.要点

* LinkedHashSet维护元素的插入顺序；
* LinkedHashSet不允许元素重复，每个元素都有唯一的值；
* 若一个元素存在，再插入相同的值，该值只会有一个存在，而且不会改变元素在插入链表中的顺序，也就是说元素在迭代遍历时的顺序不会改变；
* 注意：LinkedHashSet的性能由两个因素决定：初始化容量大小和负载因子；
* 注意：对LinkedHashSet元素的迭代时间不受容量的影响；也就是说若元素个数不变，不管容量个数是变大还是变小，迭代时间是恒定的；
* 注意：LinkedHshSet的是非线程安全的，当多个线程对其进行读写操作时，需要加锁；或则使用以下语句来对其进行保护：`Set s = Collections.synchronizedSet(new LinkedHashSet(...));`
* 若不需要维护插入元素的顺序，使用HashSet比使用LinkedHshSet更加高效。





