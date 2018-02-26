# BlockingQueue

线程信号是一种低层次，高度可配置的机制，可以适应多种用例，但也可能被认为是最容易出错的技术。因此，Java平台在线程信号机制上构建高级抽象，以解决线程间任意对象的单向切换问题。抽象通常被称为“解决生产者 - 消费者同步问题”。该问题由可能有线程产生内容（生产者线程）和线程消耗内容（消费者线程）的用例组成。生产者将消息传递给消费者进行处理。线程之间的媒介是一个阻塞行为的队列，即``java.util.concurrent.BlockingQueue`` 

![阻塞队列](https://www.safaribooksonline.com/library/view/efficient-android-threading/9781449364120/images/chapter04/blocking_queue.png.jpg)

​                                                          使用阻塞队列进行线程间通信

``BlockingQueue`` 充当生产者和消费者线程之间的协调者，将列表实现与线程信号一起包装。该列表包含生成线程用任意数据消息填充的可配置数量的元素。另一方面，消费者线程按照它们入队的顺序提取消息并处理它们。如果生产者和消费者不同步，那么生产者和消费者之间的协调是必要的，例如，如果生产者提供的消息多于消费者可以处理的消息。因此，``BlockingQueue`` 使用线程条件来确保在``BlockingQueue`` 列表已满时生产者无法入队新消息，并且消费者知道何时有消息要提取。线程之间的同步可以通过线程信号来实现，例如：``Consumer`` 和``Producer`` 所示。但``BlockingQueue`` 都会阻塞线程并发出重要状态变化的信号 - 该列表未满，列表不为空。

使用``LinkedBlockingQueue`` 实现的消费者 - 生产者模式很容易通过使用``put（）`` 将消息添加到队列中，并用``take（）`` 方法移除它们，如果队列已满，``put（）`` 阻塞调用者，如果队列为空，则``take（）`` 阻塞调用者。

```java
public class ConsumerProducer {

    private final int LIMIT = 10;
    private BlockingQueue<Integer> blockingQueue = new LinkedBlockingQueue<Integer>(LIMIT);

    public void produce() throws InterruptedException {
        int value = 0;

        while (true) {
            blockingQueue.put(value++);
        }
    }

    public void consume() throws InterruptedException {

        while (true) {
            int value = blockingQueue.take();
        }
    }
}
```