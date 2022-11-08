## :star2: Manifest, Intent, View 개념정리

1. **Manifest의 주요 속성 10가지와 4대 컴포넌트, 그리고 Intent에 대한 조사**
    - **Manifest**
        - Manifest란 앱의 패키지, 컴포넌트, 권한, 기기호환성 설정을 관리하는 파일이다.
        - 앱이 실행되기 전에 시스템이 알아야 할 내용들을 정의하고 있다.
        - **주요 속성 10가지**에는 icon, label, permission, process, taskAffinity, allowTaskReparenting, debuggable, enabled, description, allowClearUserData이 있다.
        - **4대 컴포넌트**에는 Activity, Service, BroadcastReceiver, ContentProvider가 있다.
            
            1) Activity: 사용자와 상호작용 하는 화면
            
            2) Service: 백그라운드에서 앱을 계속 실행하기 위해서 사용되는 것 ex) 백그라운드에서 음악듣기
            
            3) BroadcastReceiver: 특정 이벤트를 사용자에게 알릴 때 사용하는 것 ex) 알람 울리기
            
            4) ContentProvider: 앱 데이터에 접근하도록 해주는 것
            
            ![img](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fk.kakaocdn.net%2Fdn%2Fd6IrCs%2FbtqvXvVX8Gj%2F3zQfYcFASWlxRQcKdVuLWK%2Fimg.png)
            이미지 출처: [https://www.crocus.co.kr/1521](https://www.crocus.co.kr/1521)
            
    - **Intent**
        - 안드로이드 앱 내부 혹은 외부 컴포넌트간의 호출및 정보 전달을 하는 역할을 함.
            
            <b>1) 명시적 인텐트</b> : 인텐트를 충족하는 앱이 뭔지 지정함. 
            
            ```kotlin
            Intent intent = new Intent(this,Main2Activity.class);
            startActivity(intent);
            ```
            
            ⇒ Intent에 this(시작하고자 하는 액티비티)와 Main2Activity.class(부르고자 하는 다른 액티비티)라는 정보를 삽입하고 startActivity()에 intent를 전달하고 있음.
            
            <b>2) 암시적 인텐트</b> : 특정 컴포넌트의 이름을 대지 않지만, 대신 수행할 일반적인 작업을 선언해 다른 앱의 컴포넌트가 이를 처리할 수 있도록 해줌. 
            
            ```kotlin
            val intent = Intent(Intent.ACTION_DIAL)
            val TEST_DIAL_NUMBER = Uri.fromParts("tel", "5551212", null)
            intent.setData(TEST_DIAL_NUMBER)
            startActivity(intent)
            ```
            
            ⇒ 디바이스에 설치된 앱들 중 액션이 `ACTION_DIAL`, Uri가 `tel:5551212`인 인텐트를 처리할 수 있는 액티비티를 찾아서 실행
            
        
2. **Palette에 존재하는 View 중 자주 사용되는 요소들에 대해 조사하기**
    - **Palette**
        - 화면에 추가할 요소(버튼, 메시지)가 들어있다.
        - Common, Text, Buttons, Widgets, Layout, Containers, Goolge, Legacy 카테고리별로 다양한 컴포넌트들이 존재한다.
    
    - **View**
        - Palette → Layout 파일 만들면 왼쪽에 나오는 TextView, ImageView와 같은 배치할 수 있는 View 목록
        - **View**는 사용자의 눈에 보이는 화면의 구성 요소들로, 일반적으로 컨트롤이나 위젯으로 불리는 UI 구성 요소이다. 뷰를 여러 개 포함하고 있는 것은 ViewGroup이라고 칭한다.
            - View 조사
                1. TextView: 문자열 표시 
                2. Button: 버튼 표시 
                3. ImageView: 이미지 출력 
                4. RecyclerView: 사용자가 관리하는 많은 수의 데이터 집합(Data Set)을 개별 아이템 단위로 구성하여화면에 출력하는 뷰그룹(ViewGroup)
                5. FragmentContainerView: FrameLayout을 확장하여 프래그먼트 트랜잭션을 안정적으로 처리
                6. ScrollView: 여러개의 컴포넌트(components)와 뷰(views)를 담을 수 있는 스크롤 컨테이너
                7. Switch: 두 가지 옵션 중 하나를 선택할 수 있는 두 개의 상태 Toggle Switch
                8. ImageButton: 일반 Button 에 custom image 를 보여주기 위해 사용
                9. ChipGroup & Chip: 키워드 혹은 카테고리, 요소, 타입 등을 표현 할 때 종종 타원형의 background에 그 텍스트를 표현
                10. CheckBox: 체크박스로 표현 
                11. RadioGroup & RadioButton: 여러 종류의 선택 항목에서 한 가지만 선택하는 형태의 버튼 
                12. FloatingActionButton: 화면에 떠있는 원형의 버튼
                13. WebView: 프레임워크에 내장된 웹 브라우저 컴포넌트로 뷰(View)의 형태로 앱에 임베딩
                14. ProgressBar: 진행막대
                15. SeekBar: 프로그레스바를 상속받은 상태표시 위젯
                16. Spinner: 사용자가 여러 선택지 중 하나를 고르게 하고 싶을 때 사용하는 위젯
                17. HorizontalScrollView: 수평방향 스크롤뷰
                18. NestedScrollView: ScrollView와 비슷하지만 부모와 자식 사이에서의 중첩 스크롤을 지원
        - **Widget**은 뷰 중에서 일반적인 컨트롤의 역할을 한다.
        - **Layout**은 뷰그룹 중에서 내부에 뷰들을 포함하고 있으면서 그것들을 배치하는 역할을 한다. 다음은 대표적인 레이아웃이다.
            
            1) ConstraintLayout(제약 레이아웃): 제약 조건 기반 모델. 뷰의 크기와 위치를 결정할 때 제약 조건을 사용한다.
            
            제약 조건이란 뷰가 레이아웃 안의 다른 요소와 어떻게 연결되는지 알려주는 것으로, 뷰의 Anchor Point(연결점)과 Target(대상)을 연결한다.
            
            2) LinearLayout(리니어 레이아웃): 박스 기반 모델. 한 쪽 방향으
            
            3) RelativeLayout(상대 레이아웃): 규칙 기반 모델. 부모 컨테이너나 다른 뷰와의 상대적 위치로 화면을 구성한다.
            
            4) FrameLayout(프레임 레이아웃): 싱글 모델. 가장 상위에 있는 하나의 뷰 또는 뷰 그룹만 보여준다.
            
            5) TableLayout(테이블 레이아웃): 격자 모델. 격자 모양의 배열을 이용하여 화면을  구성한다.
