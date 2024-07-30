```dart
import 'package:flutter/material.dart';

void main() {
  //플러터 앱을 실행한다.
  runApp(
    //MaterialApp은 항상 최상위에 위치
    //Scaffold는 바로 아래에 위치
    //MaterialApp, Scaffold, Center, Text 등등은 Widget임
    //각 위젯에서 cmd+b 누르면 해당 위젯 정의 볼 수 있음
    //배경은 Scaffold에서 지정
    MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        backgroundColor: Colors.blueAccent,
        body: Center(
          child: Text('Hyewon',
              style: TextStyle(
                color: Colors.white,
              )),
        ),
      ),
    ),
  );
}
```

<img src="https://github.com/user-attachments/assets/4e94d6ee-2884-4a1f-bb3d-216afda7b72b" width="450" alt="Simulator Screenshot">
