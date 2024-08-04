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