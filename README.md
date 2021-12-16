# MYONGJICOLLEGEDdictionary
소프트웨어콘텐츠-2021661089-정시안 앱 개발기초-기말고사 보고서

앱 설명
- 명지전문대 사전을 만들어 위치, 가는 방법, 캠퍼스 소개, 각종 학부를 정리하였습니다.

앱 개발 내용 설명
- activity_main.xml에서는 LinearLayout으로 바꿔주었습니다.
ImageView를 사용해 이미지를 가져와 메인화면 앞에 로고를 만들어주었습니다.
TextView를 사용해 이미지 옆에 제목을 text로 만들어주고 배경, 글씨의 색을 넣고 가운데로 옮겨주었습니다.
RecyclerView 안에 있는 클래스인 ViewHolder의 재사용성을 위해 ListView가 아닌 RecyclerView를 사용해 주었습니다.

- activity_mjc.xml에서도 LinearLayout으로 바꿔주었습니다.
Button을 만들어주어 다른 단어도 보고 싶을 때 돌아가기 버튼을 눌러 다른 것도 볼 수 있도록 하였습니다.
TextView를 사용해서 itemTitle이라는 id를 만들고 크기와 색상, 위치를 설정하여 MjcActivity에서 사용하기 위해 만들었습니다.
ImageView 역시 “명지전문대 캠퍼스 소개”의 이미지를 넣어주기 위해 만들었습니다.
2번째 TextView 역시 MjcActivity에서 사용하기 위해 itemText이라는 id를 만들고 크기와 색상, 위치를 설정하여 만들었습니다.

-list_item.xml은 LinearLayout으로 적용하였고 따로 RecyclerView 안에 적용하기 위해 만들어주었습니다.

RecyclerView파일을 따로 만들어주어 정리하였습니다.
-ItemClickListener 인터페이스를 만들어 아이템을 클릭시 실행되는 함수을 만들어주었습니다.

- Myadapter는 목록 화면의 아이템과 뷰를 관리하는 영역으로 ListItem이 터치되었을 때 동작하게 되는 이벤트리스너 메소드에 액티비티를 전환하는 코드를 넣었습니다.
onCreateViewHolder(), onBindViewHolder(), getItemCount() 메서드를 넣었습니다.
Activity(화면페이지)를 전환하는 방법으로 Intent를 쓰고 있습니다.
Activity 전환(화면전환)하기 위해서는 정보와 권한이 필요하기에 context가 필요합니다.
MjcActivity를 표출할 것이기 때문에 context와 MjcActivity.class를 전달하여 Intent를 생성합니다.
새 액티비티에는 보여줄 각 리스트 항목의 제목과 순번이 필요하므로 Intent에 정보를 담아줍니다.

- ViewHolder는 list_item.xml 안에 있는 위젯을 보관하는 클래스로 ViewHolder를 사용하지 않으면 목록 화면을 스크롤하는 동안 findViewById()를 여러번 호출하게 되어 문제가 생기기에 만들어줍니다.

- MainActivity
MainActivity안에 데이터를 전달하고 RecyclerView에 Adpater를 연결시키도록 하였습니다.
setHasFixedSize()에서는 목록의 개수가 변경될 가능성이 없어 ture로 설정하였습니다.
setLayoutManager는 각 목록 화면을 어떤식으로 배치할지 결정하는 메소드로 
(new LinearLayoutManager(this)); 작성하였습니다.
메인화면에 들어갈 list의 제목을 작성해주었습니다.

- mjcActivity
각 리스트 아이템의 설명을 맡은 Activity입니다.
Activity가 생성되며 실행되는 onCreate 의 내부에 추가 코드를 넣었습니다.
MainActivity에서 전달받은 Intent 안에서 MainActivity에서 넣어준 정보들을 빼냅니다.
intent.getStringExtra 등의 메소드로 터치된 아이템의 제목과 순번을 알 수 있습니다.
그 후 순번별로 문자열 리소스를 가져와서 TextView에 넣어줍니다.
순번별로 구분하는 방법 중 저는 switch case 문을 사용하였습니다.
3번째 리스트 항목인 캠퍼스 안내의 경우에는 캠퍼스 이미지도 보여줘야하기 때문에 
case2: 의 경우는 ImageView에 이미지를 할당하는 코드가 더 있게 됩니다.
다른 항목들과 다르게 건물 안내 문자열들이 center 정렬보다 왼쪽정렬로 만들어주었습니다.
