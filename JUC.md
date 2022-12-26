### wait/sleep区别

1. 来源不同

   wait是Object实例方法

   sleep是Thread的静态方法

2. 锁的释放

   wait会释放锁，

   sleep不会释放锁

3. 使用地方

   wait在同步代码或者同步代码块中使用，不需要捕获异常

   sleep可以在任何地方使用，需要捕获异常

4. 唤醒方式

   wait需要被notify或者notifyAll方法

   sleep需要等待时间结束或者使用Interrupt()方法