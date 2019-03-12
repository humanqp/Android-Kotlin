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
  - NPE에 안전한 변수 선언 방법
  ```kotlin
  //? null 허용
  var a:String? = "abc"
  a = null
  ```
  ```kotlin
  //null 일 때 초기화 지정
  var a:String? = "abc"
  a = null
  var len:Int = a?.length?:0
  ```
  ```kotlin
  //!!을 참조할 수 있도록 허용
  var a:String? = "abc"
  a = null
  var len:Int = a!!.length //null을 참조하기 때문에 exception이 나게 됨
  ```
  - == , ===(pointer까지 같은지 확인) 연산자 

> ### 람다
  - add 함수를 람다로 구현
  ```kotlin
  (x,y)->x+y
  ```
  - 언더스코어( _ ) : 사용하지 않은 인자 처리.
  - inline 키워드 : 함수 호출을 하지 않고 코드를 그래로 프로그램 중 실행 함.
  
> ### 제네릭
  - 와일드 카드(?) : 모든 객체 대입 가능 
  - Ex> java extends 하위 제한 
  ```java
  public <T> void copy(List<T> dest, List<? extends T> src) {
    for(T item:src){
      dest.add(item);
    }
  }
  ```
  - Ex> kotlin
  ```kotlin out 하위 제한 
  fun copy(dest:List<T>, src:List<out T>{
    for(item:T in src){
    
    }
  }
  ```
  - Ex> java super -> kotlin in 상위 제한
  ```kotlin
  fun <T> fill(list: List<in T>, obj: T){
    val size = list.size
    
  }
  ```
  ```kotlin
  class Person{
  
  }
  class PersonType<in Person>{
  
  }
  ```
  
> ### 그 밖의 유용한 함수들
  - apply() : block으로 정의된 구간을 수행하고 apply를 사용한 객체를 다시 반환해줍니다. 특징, 리턴값으로 인자를 넘겨 줌
  ```kotlin
  fun setWindowParam(){
    window.attributes = WindowManager.LayoutParams().apply{
      flags = WindowManager.LayoutParams.FLAG_DIM_BEHIND
      dimAmount = 0.8f
  }
  ```
  - run() : 어떤 경우에는 어떤 인스턴스에 관련된 필드나 메서드에 연속적으로 접근해야할 때가 있습니다. 이런 경우 run을 쓸 수 있습니다.
            run() = with() + let()을 혼합해 놓은 함수 임.
  ```kotlin
  class RepoViewHolder(private val view: View): RecyclerView.ViewHolder(view) {
    fun setRepo(repo: Repository) {
      view.run {
        //view 내의 필드나 메서드를 대한 접근이 암목적으로 허용되기 때문에, findViewById 사용 가능.
        findViewById(R.id.fg).setOnClickListener {
          val message = repo.run {
            "\n".join(fullName, language)
          }
          Toast.makeText(view.context, message, Toast.LENGTH_SHORT).show()
        }
        ...
      }
    }
  }
  ```
  - let() : let은 값이 있는 경우에 다른 코드 블록을 추가로 수행하는 것입니다.
  ```kotlin
  override fun onBindViewHolder(holder: RepoViewHolder?, position: int) {
    repos.getOrNull(position)?.let {
      holder?.setRepo(it)
    }
  }
  ```
  - with() : 기존의 함수들과 다르게 넘기려는 객체를 괄호 안에 넣어 주고 {}를 수행하도록 함. 
  ```kotlin
  with(convertView){
    findViewById(R.id.add).setOnClickListerner{
      Toast.makeText(context, "Clicked", Toast.LENGTH_SHORT).show()
    }
  }
  ```
 - forEach() : for문을 사용하지 않고 콜렉션에 바로 접근해서 사용할 수 있음.
 ```kotlin
 fun getDataIndex(data: ArrayList<WeekList>):Int {
  val current:Long = Date().time
  (0..data.size-1).forEach{
    if(current < data[i].dt.toLong()){
      return i;
    }
  }
 }
 ```
 - onEach() : forEach 함수와 비슷하며, {}안에 취한 행동의 결과값을 반환 측면에서 조금 다름.
 ```kotlin
 fun getListSize(list:Array<Persion>):Int = list.filter{it.age >= 30}
    .onEach{ Toast.makeText(this, "Hello ${it.name}", Toast.LENGTH_SHORT).show() }.size
 ```
 - fillter() : 콜렉션의 filter 함술르 사용 할 때 
 ```kotlin
 fun addOdd():Int{
  var result = 0;
  //1~50까지 중 홀수만 필터하여 forEach로 전달하고 해당 내용을 합산하여 return 함.
  (1..50).filter { (it%2 - 1) == 0 }.forEach { result += it}
  return result
 }
 ```
 - lazy() : 변수가 선언되는 시점에 초기화를 진행하지 않고 사용되는 시점에 생성이 되도록 함.
 ```kotlin
 class MainActiviy : AppCompatActivity(){
  val toolbar: Toolbar by lazy{
    findViewById(R.id.toolbar) as Toolbar
  }
  override fun onCreate(savedInstanceState: Bundle?){
    toolbar.setTitle("")
  }
 }
 ```
 - lateinit : var만 사용 가능 >> 확인 필요.
 ```kotlin
 class MainActiviy : AppCompatActivity(){
  
  lateinit var toolbar: Toolbar
  
  override fun onCreate(savedInstanceState: Bundle?){
    setContentView(R.layout.activity_main) 
    toolbar = findViewById(R.id.toolbar) as Toolbartoolbar.setTitle("")
  }
 }
 ```
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
  
    
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
    
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
