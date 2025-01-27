# Imadeddin Ouahidi
## Lasagna 

I love Lasagna because it’s **flavorful** and **cheezy**. It always reminds me of my **childhood memories**.

---

## About Lasagna:

1. Home cooked by mom
2. An Italian restaurant
3. Frozen from a supermarket

- Ceasar salad
- Grilled vegetables
- Garlic bread

[My favorite movie](MyMovie.md)

---

## Alternative Actors for The Wolf of Wall Street

While Leonardo DiCaprio gave an iconic performance in *The Wolf of Wall Street*, here are some other actors that I want to see play the main role besides Leonardo DiCaprio:

| Actor Name        | Reason                              | Age |
|-------------------|-------------------------------------|-----|
| Christian Bale    | Known for his intense and transformative acting | 50  |
| Matthew McConaughey | Charismatic and skilled at portraying eccentric characters | 55  |
| Tom Hardy         | Dynamic and great with high-energy roles | 47  |
| Bradley Cooper    | Captivating presence and strong comedic timing | 50  |

---

## Favorite Quotes

> "Two things are infinite: the universe and human stupidity; and I'm not sure about the universe."  
*Albert Einstein*

> "Be the change that you wish to see in the world."  
*Mahatma Gandhi*

---

## Python Code

Here is a snippet of Python code that creates a thread pool(based on 75 as the two last digits of my S number):

```python
import threading
import time
from queue import Queue


def f(n):
    time.sleep(n)


class Worker(threading.Thread):
    def __init__(self, queue):
        super(Worker, self).__init__()
        self.q = queue
        self.daemon = True
        self.start()

    def run(self):
        while 1:
            f, args, kwargs = self.q.get()
            try:
                f(*args, **kwargs)
            except Exception as e:
                print(e)
            self.q.task_done()


class ThreadPool(object):
    def __init__(self, thread_num=10):
        self.q = Queue(thread_num)
        for i in range(thread_num):
            Worker(self.q)

    def add_task(self, f, *args, **kwargs):
        self.q.put((f, args, kwargs))

    def wait_complete(self):
        self.q.join()


if __name__ == '__main__':
    start = time.time()
    pool = ThreadPool(5)
    for i in range(10):
        pool.add_task(f, 3)
    pool.wait_complete()
    end = time.time() 
```
[Link for the snippet source](https://code.pieces.app/collections/python)
