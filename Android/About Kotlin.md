# Kotlin

람다(Lambda expression)
1. 중괄호로 감싼다
2. 인자와 본문은 ->로 구분한다
3. 인자는 ()로 감싸지 않는다.
4. 인자는 형식추론이 가능하므로 타입을 생략할 수 있다.
5. 변수에 람다식을 담는경우에는 인자의 타입을 생략할 수 없다.
```
fun main(args: Array) {
    val sum = { x: Int, y: Int -> println("Computing the sum of $x and $y...")
         x + y 
    }
     println(sum(1, 2)) 
}
```

```for ( i in 0 until cnt )``` i를 0부터 cnt전까지 반복



lateinit / 늦은 초기화 / 선언과 동시에 초기화 할 필요가 없음