# Splash Screen
: 앱을 시작할 때 대기해야 되는 시간동안 보여주는 스크린

## <p style="color:skyblue">주요 포인트</p>
1. StatelessWidget 사용법
2. Asset 이미지 등록법
3. Image 위젯 사용법
4. Column 위젯 사용법
5. HexCode 색상 사용법
6. CircularProgressIndicator 위젯 사용법
7. Padding 위젯 사용법
8. SizedBox 위젯 사용법

### YAML 구조

플러터 프로젝트 생성하면 pubspec.yaml이라는 파일이 있음(플러터 프로젝트 관련 세팅을 전부 담당)

- YAML : 사람이 쉽게 읽고 쓸 수 있는 데이터 직렬화 언어. 주로 설정 파일이나 데이터 전송 형식으로 사용되며 들여쓰기를 통해 계층 구조를 표현함

- image 사용시에도 pubspec.yaml 파일에 추가해줘야함
```yaml
  flutter:  # 플러터 key 안에 넣어주기

  # The following line ensures that the Material Icons font is
  # included with your application, so that you can use the icons in
  # the material Icons class.
  uses-material-design: true

  assets:
    - asset/img/        # asset폴더의 img 폴더의 이미지 모두 사용가능
```
- 변경 후 우측 상단 Pub get 눌러야 변경된 사항 적용됨(콘솔에 exit code 0 나오면 성공, 1이 나오면 실패)

### <p style="color:skyblue">Asset 이미지 등록법</p>
```dart
import 'package:flutter/material.dart';

void main() {
  runApp(
    MaterialApp(
      home: Scaffold(
        backgroundColor: Colors.blue,
        body: Image.asset('asset/img/logo.png'),
      ),
    ),
  );
}
```

### <p style="color:skyblue">HexCode 색상 사용법</p>
- 구글에 color picker 검색해서 rgb 색상 선택 가능
- Colors. 하면 Material.Dart에서 기본으로 제공해주는 색상 선택 가능하고,
<br>
정확한 색상 표현하고 싶으면 Color 클래스를 인스턴스화하여 값 넣어주기
```dart
    /// 335CB0
    backgroundColor: Color(0xFF335CB0),   //0xFF 무조건 붙여주기
```

### <p style="color:skyblue">Column 위젯 사용법</p>
```dart
    body: Center(
        child : Image.asset('asset/img/logo.png'),      //child위젯은 하나만 입력 가능
    ),
```
- Column위젯 : 세로로 children파라미터에 있는 위젯들을 배치할 수 있음
- mainAxisAlignment를 변경함으로써 세로로 어떻게 정렬할지 정할 수 있음
```dart
    body: Column(
        mainAxisAlignment: MainAxisAlignment.center,    //주축에서 정렬
        children: [   //list라 여러개 등록 가능
        Image.asset('asset/img/logo.png',)
        ],
    ),
```

### <p style="color:skyblue">CircularProgressIndicator 위젯 사용법</p>
기본으로 제공되는 위젯이 많아 유용함
```dart
    body: Column(
        mainAxisAlignment: MainAxisAlignment.center,    //주축에서 정렬
        children: [   //list라 여러개 등록 가능
        Image.asset('asset/img/logo.png',),
        CircularProgressIndicator(
            color: Colors.white,
        ),
        ],
    ),
```

### <p style="color:skyblue">StatelessWidget 사용법</p>
위젯 만들기

1. 클래스명 짓기
```dart
class HomeScreen extends StatelessWidget {    //위젯에 해당되는 클래스인걸 알려주기 위해 extends
}
```
- StatelessWidget는 Material.dart에서 불러올 수 있는 것임
- 모든 StatelessWidget은 가장 기본적으로 build 함수 존재해야함
<br>
<br>

2. build 함수(자동완성됨)
```dart
@override
  Widget build(BuildContext context) {
    // TODO: implement build
    throw UnimplementedError();
  }
```
- 여러개의 widget을 하나의 widget으로 묶는 역할 할 수 있음
<br>
<br>

3. build 함수의 정의(Scaffold 반환)
```dart
@override
  Widget build(BuildContext context) {
    return Scaffold(
      /// 335CB0
      backgroundColor: Color(0xFF335CB0),   //0xFF 무조건 붙여주기
      body: Column(
        mainAxisAlignment: MainAxisAlignment.center,    //주축에서 정렬
        children: [   //list라 여러개 등록 가능
          Image.asset('asset/img/logo.png',),
          CircularProgressIndicator(
            color: Colors.white,
          ),
        ],
      ),
    );    //마지막은 세미콜론
  }
```
<br>
<br>

4. 일반 위젯처럼 사용
```dart
import 'package:flutter/material.dart';

void main() {
  runApp(
    MaterialApp(
      home: HomeScreen(),
    ),
  );
}

/// StatelessWidget
class HomeScreen extends StatelessWidget {    

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      /// 335CB0
      backgroundColor: Color(0xFF335CB0),   //0xFF 무조건 붙여주기
      body: Column(
        mainAxisAlignment: MainAxisAlignment.center,    //주축에서 정렬
        children: [   //list라 여러개 등록 가능
          Image.asset('asset/img/logo.png',),
          CircularProgressIndicator(
            color: Colors.white,
          ),
        ],
      ),
    );    //마지막은 세미콜론
  }
}
```
- StatelessWidget을 상속받는 어떤 하나의 클래스를 만들기만 하면 여러개의 위젯을 한번에 보여줄 수 있는 위젯을 새로 정의할 수 있음

** stless 단축어 사용
: StatelessWidget을 좀 더 간단하게 선언할 수 있음
```dart
class HomeScreen extends StatelessWidget {      //클래스명 주면 생성자까지 자동으로 클래스명 입력됨
    const HomeScreen({super.key});        //자동 생성됨

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      /// 335CB0
      backgroundColor: Color(0xFF335CB0),   //0xFF 무조건 붙여주기
      body: Column(
        mainAxisAlignment: MainAxisAlignment.center,    //주축에서 정렬
        children: [   //list라 여러개 등록 가능
          Image.asset('asset/img/logo.png',),
          CircularProgressIndicator(
            color: Colors.white,
          ),
        ],
      ),
    );  
  }
}
```

### <p style="color:skyblue">Padding 위젯 사용법</p>
- padding은 위젯 하나만 받음
```dart
body: Padding(
    padding: EdgeInsets.symmetric(    //symmetric : 대칭
        horizontal: 32.0,
    ),   //padding 파라미터 입력 필수
    child:Column(
        mainAxisAlignment: MainAxisAlignment.center,    
        children: [   
        Image.asset('asset/img/logo.png',),
        CircularProgressIndicator(
            color: Colors.white,
        ),
        ],
    ),
),
```

**hot reload
- 앱 전체를 다시 시작하지 않더라도 runApp 안의 모든 위젯들의 build함수 재실행 가능
- 스크린이 여러개일 때 유용
- 수정 사항이 build함수 외부라면 재실행, 내부라면 hot reload 가능

### <p style="color:skyblue">SizedBox 위젯 사용법</p>
SizedBox : 크기가 있는 박스, padding과 비슷
```dart
SizedBox(height: 28.0),     //높이 28인 박스
```

<img src="https://github.com/user-attachments/assets/39f5eb76-a340-4d5e-9b35-bbd894dc920f" width="450" alt="Simulator Screenshot">

### Show Context Action
1. 삭제하고싶은 위젯이 있을 때
- 해당 위젯 위에 커서를 두고 우측클릭해서 Show Context Action 또는 단축키 누른 후 remove

2. 추가할 때
- 단축키 누른 후 Wrap with widget 후 위젯 입력