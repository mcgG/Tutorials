async

* non-blocking sockets
* callbacks
* event loop

select, poll, epoll





协程看上去像子程序，但是在执行过程中在子程序内部可中断，然后转而执行别的子程序，在适当的时候再返回来接着执行

在一个子程序中中端，去执行其他程序，不是函数调用，有点类似CPU的中断



协程看起来有点像多线程，但协程的特点在于是一个线程执行，那和多线程比，协程有何优势？

* 协程有极高的执行效率，因为子程序不是线程切换，没有上下文切换开销，和多线程比，线程数量越多，协程的性能优势越明显。
* 不需要线程的锁机制，因为只有一个线程，也不存在同时写变量冲突，在协程中控制共享资源不加锁，只需判断状态就好了，所以执行效率比线程高很多。

因为协程是一个线程执行，那么怎么利用多核CPU呢？最简单的方法是**多进程+协程。**

Python对协程的支持是通过generator实现的

在generator中，我们不但可以通过`for`循环来迭代，还可以不断调用`next()`函数获取由`yield`语句返回的下一个值。

但是Python的`yield`不但可以返回一个值，它还可以接收调用者发出的参数。

来看例子：

传统的生产者-消费者模型是一个线程写消息，一个线程取消息，通过锁机制控制队列和等待，但一不小心就可能死锁。

如果改用协程，生产者生产消息后，直接通过`yield`跳转到消费者开始执行，待消费者执行完毕后，切换回生产者继续生产，效率极高：

```py
def consumer():
    r = ''
    while True:
        n = yield r
        if not n:
            return
        print('[CONSUMER] Consuming %s...' % n)
        r = '200 OK'

def produce(c):
    c.send(None)
    n = 0
    while n < 5:
        n = n + 1
        print('[PRODUCER] Producing %s...' % n)
        r = c.send(n)
        print('[PRODUCER] Consumer return: %s' % r)
    c.close()

c = consumer()
produce(c)
```



