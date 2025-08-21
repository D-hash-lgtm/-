#项目名称
线程分配![1741597202270](https://github.com/user-attachments/assets/d6614d40-d5b7-4b4d-b58d-7c0490abff1a)
以下是一个Java多线程的简单示例代码，展示了通过继承 Thread 类和实现 Runnable 接口两种创建线程的方式：

1. 继承Thread类创建线程


// 继承Thread类并重写run()方法
class MyThread extends Thread {
    private String threadName;

    public MyThread(String name) {
        this.threadName = name;
    }

    @Override
    public void run() {
        // 线程执行的任务
        for (int i = 0; i < 5; i++) {
            System.out.println(threadName + " 执行: " + i);
            try {
                // 线程休眠100毫秒，模拟任务耗时
                Thread.sleep(100);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
        System.out.println(threadName + " 执行完毕！");
    }
}
 

2. 实现Runnable接口创建线程


// 实现Runnable接口
class MyRunnable implements Runnable {
    private String taskName;

    public MyRunnable(String name) {
        this.taskName = name;
    }

    @Override
    public void run() {
        // 线程执行的任务
        for (int i = 0; i < 5; i++) {
            System.out.println(taskName + " 执行: " + i);
            try {
                Thread.sleep(100);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
        System.out.println(taskName + " 执行完毕！");
    }
}
 

3. 测试线程执行


public class ThreadDemo {
    public static void main(String[] args) {
        // 方式1：通过Thread子类创建线程
        MyThread thread1 = new MyThread("Thread-1");
        thread1.start(); // 启动线程（底层调用run()方法）

        // 方式2：通过Runnable接口创建线程（推荐，解耦任务与线程）
        MyRunnable runnable = new MyRunnable("Runnable-Task");
        Thread thread2 = new Thread(runnable, "Thread-2");
        thread2.start();

        // 主线程执行
        for (int i = 0; i < 5; i++) {
            System.out.println("Main线程 执行: " + i);
            try {
                Thread.sleep(100);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
        System.out.println("Main线程 执行完毕！");
    }
}
 

输出说明

- 线程的执行顺序是不确定的（由CPU调度决定），因此每次运行输出结果可能不同。
- 关键方法： start() （启动线程）、 run() （线程任务逻辑）、 sleep(long millis) （线程休眠）。

如果需要其他语言（如Python、C++）的线程代码，或者更复杂的线程同步(https://m.baike.com/wikiid/1710915976696282076?baike_source=volc_feed&ttwebview_extension_mixrender=1&__pia_mixrender_logger__=1&pia_mixrender=1)（如 [synchronized](https://m.baike.com/wikiid/8854546549219260078?baike_source=volc_feed&ttwebview_extension_mixrender=1&__pia_mixrender_logger__=1&pia_mixrender=1) 、 Lock ）示例，可以告诉我哦！
