# Android Kotlin
> ### Kotlin 아름다운 기능들 : https://academy.realm.io/kr/posts/kotlin-let-run-apply-lateinit/

> ### vararg
  - 다양한 변수 값을 하나의 변수로 전달 받을 때 사용 함
  ```kotlin
  fun add(varage numbers:Int):Int 
  {
    var total:Int = 0
    for(n in numbers)
      total +=n
    return total
  }
  ```
> ### 흐름 제어 연산자
  - 1<i<10
  ```kotlin
  for(i in 2..9){
  }
  ```
  - 10>i>1
  ```kotlin
  for(i in 9 downTo 2){
  }
  ```
  - 1<i<10 i+2
  ```kotlin
  for(i in 2..9 step 2){
  }
  ```
  - 11<i<1 i-2
  ```kotlin
  for(i in 10 downTo 1 step 2){
  }
  ```
  
  
