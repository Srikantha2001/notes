
## Default Lock :

- By Default , java uses the `synchronized` block or method to allow only one thread to execute critical section at a time. It internally uses <mark style="background: #D2B3FFA6;">monitor lock</mark> to lock the object.
- Disadvantages : 
	- Lack of Flexibility : always applies at method level
	- Lock at <mark style="background: #FFF3A3A6;">object level</mark> : if there are multiple objects involved, they can execute critical section simultaneously.
	- No concept of Fairness : 
	- Thread in <mark style="background: #ADCCFFA6;">waiting state</mark> are uninterruptible.


### Explicit Locks

- There are the flexible locks provided by Java.
- Code related to same is present in <mark style="background: #FFB8EBA6;">java.util.concurrent.Locks</mark>
- Generic Code of Explicit Locks looks something like this
```Java
Lock l = ...;
l.lock();
try {
  // access the resource protected by this lock (critical Section)
} finally {
  l.unlock();
}
```

![Lock Interface.png](../../Resources/Lock%20Interface.png)

- There are mainly 4 types of explicit locks
	- ReentrantLock
	- ReadWriteLock
	- StampedLock
	- Semaphores

#### ReentrantLock

```Java
class X {
  private final ReentrantLock lock = new ReentrantLock();
  // ...

  public void m() {
    lock.lock();  // block until condition holds
    try {
      // ... method body
    } finally {
      lock.unlock();
    }
  }
}
```
