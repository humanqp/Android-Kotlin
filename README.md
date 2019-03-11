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
> ### 
