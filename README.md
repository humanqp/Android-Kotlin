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
  - list size
  ```kotlin
  for(i in 0..data.size-1){
  }
  ```
  - list iterator
  ```kotlin
  var nameList:Array<String> = arrayOf("A","B","C")
  for(name:String in nameList){
  
  }
  ```
  - switch 대신 when
  ```kotlin
  override fun onClick(v:View?){
    when(v?.id){
      R.id.search_button ->{
      }
      R.id.search_go_bth ->{
      }
    }
  }
  ```
  
  ```kotlin
  //when에 지정된 값이 없는 경우 연산으로 사용 가능.
  fun Test(number:Int){
    when{
      조건1->결과1
      조건2->결과2
      조건3->결과3
    }
  }
  ```
  
> ### 콜렉션
  - listOf
  ```kotlin 
  val nameList = listOf("A","B","C")
  for(i in 0..nameList.size-1){
  }
  ```
  - mutableListOf
  ```kotlin
  var nameList = mutableListOf<String>()
  if(nameList.isEmpty()){
    nameList.add("No Name")
  }
  ```
  - 콜렉션 null filterNotNull
  ```kotlin
  val nameList = listOf("A","B","C")
  for(name in nameList.filterNotNull()){
    print(name)
  }
  ```
  - 콜렉션 + - : 콜렉션 내용을 추가, 삭제 할 수 있음 p66
  
> ### 타입 체크와 비교 연산
  - 타입 체크 : is
  ```kotlin
  if(view is LinearLayout){
  }
  ```
  - 타입 캐스팅 as
  ```kotlin
  var param:LinearLayout.LayoutParams = view.layoutParams as LinearLayout.LayoutParams
  ```
  - 
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
