# Android Libirary

- 눈에 보이는지
```
.visibility = GONE
.visibility = VISIBLE
.visibility = INVISIBLE
```

- Textview 뒤에 단어 추가 
```
.append
```

## Recycler View
- inflater
<br>xml로 정의된 view (또는 menu 등)를 실제 객체화 시키는 용도입니다.
예를 들어 약간 복잡한 구조의 view를 java코드로 만들게 되면 생성하고 속성 넣어주느라 코드가 길어질 수 있는데,
그걸 미리 xml로 만들어 놓고 java코드에서는 inflater를 활용하여 바로 view를 생성할 수 있습니다.

- adapter
<br>ListView (또는 다른 형태의 ViewGroup) 와 실제 데이터(List, Array 등)의 중간 역할을 하는 추상 인터페이스 입니다.
ListView에서는 실제 데이터가 어떤 형태인지 어떤 데이터들을 가지고 있는지 상관하지 않고 adapter가 주는 view만
 목록으로 나열하게끔 되어 있고, 실제 데이터 역시 어떻게 표현할지 관심 가지지 않고, adapter에서 원하는대로 
데이터만 주면 되도록 서로 분리시키는 것입니다. adapter가 할 일은 실제 데이터 관리를 하고 ListView가 
'보여질 목록하나 만들어줘라 (getView)' 할때 실제 데이터에서 view를 만들어서 주는 역할입니다.​

Adapter 클래스 생성 (RecyclerView를 상속받음)

 1. onCreateViewHolder(ViewGroup, viewType) : 뷰홀더와 레이아웃 파일을 연결해주는 역할
     - ViewGroup : 
     - viewType : 레이아웃 타입의 종류를 지정해줄 수 있음
     
 2. getItemCount : 리사이클러뷰안에 들어갈 뷰 홀더의 개수
   
 3. onBindViewHolder : 어댑터라는 존재가 필요한 만큼 뷰 홀더를 생성하고, 뷰 홀더안에 표시할 데이터와 연결시켜준다. 뷰홀더가 필요한 위치가 할당 될 때, 어댑터는 onBindViewHolder를 호출


- LayoutManager 
<br>RecyclerView의 아이템 배치와 재사용에 대한 정책을 결정하면 LayoutManager의 종류에 따라 아이템의 배치가 변경됩니다.
Recycler view 안에있는 item view들을 조절하고 자리잡게 해주는 녀석임. 더이상 사용자들에게 보이지 않는 item view들을 재사용하기 위한 
정책을 결정해준다.

- xmls:tools 쓰는이유?
<br>textAppearance ? >> color, typeface, size, style을 한번에 설정 >> 프레임워크에 정의된 값을 지정 >> R.attr에 "textAppearanceXXX" 형식으로 명명된 값 사용.

- onActivityResult
<br>startActivityForResult로 날린값을 받아줌. A->B->A로 올때 B 데이터를 A에서 받아줌

- setHasFixedSize
<br>데이터가 변했을때 성능을 높일 때 사용. 
각 Item 들이 RecyclerView 의 전체 크기를 변경하지 않는 다면 setHasFixedSize() 함수를 사용해서 성능을
개선할 수 있습니다. 변경될 가능성이 있다면 false 로 , 없다면 true를 설정.

- setOnTouchListener vs setOnClickListener
<br>setOnTouchListener : 사용자의 손가락 방향, 드래그 등 행동에 맞게 구현, 이벤트설정 가능
<br>setOnClickListener : 단순 클릭 이벤트

- data class : 데이터만을 담기위한 클래스
- notifyDataSetChanged() : 어댑터에 연결된 view를 갱신함

## SharedPreferences
- sharedPreferences : xml파일에 필요한 데이터를 저장하여 쉽게 읽고 쓰게 하는것
<br>경로 : data/data/패키지명/shared_prefs/SharedPrefenrece에 파일 저장
- getSharedPreferences(String name, int mode) 를 통하여 객체를 받아올 수 있음
<br>name : SharedPreferences의 이름
<br>mode : 읽고 쓰기 권한 관련된 Mode
