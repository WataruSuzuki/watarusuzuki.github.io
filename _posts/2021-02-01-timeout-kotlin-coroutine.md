---
layout: post
title:  "TimeoutをKotlin Coroutinesで"
tags:
- Engineer-Life
- Study
- Android

---

公式にちゃんと[Timeout](https://kotlinlang.org/docs/reference/coroutines/cancellation-and-timeouts.html#timeout)の例がある。すごく書きやすい感じ。

```kotlin
withTimeout(1300L) {
    repeat(1000) { i ->
        println("I'm sleeping $i ...")
        delay(500L)
    }
}
```

----------
#### 参考
- [Cancellation and Timeouts](https://kotlinlang.org/docs/reference/coroutines/cancellation-and-timeouts.html)
