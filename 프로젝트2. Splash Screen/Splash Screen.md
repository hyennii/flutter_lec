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