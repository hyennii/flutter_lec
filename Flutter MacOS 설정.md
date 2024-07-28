## 1. 사양 확인

[flutter.dev](http://flutter.dev) 진입 → 우측 상단 Get started 들어가서 macOS 클릭하면 설치 가이드 확인 가능

** http://links.codefactory.ai 들어가서 최하단 ‘mac 설치 교안’ 들어가면 사용할 커맨드들 정리되어 있어 참고 가능

- 시스템 운영 체제 : macOS,  10.14 버전(Mojave) 이상
- 용량 : 최소 2.8GB (플러터 SDK 설치하는데 2.8GB이고, 프로젝트나 다른 IDE들 포함 안 한 값) / 최소 10GB 이상 추천
- 플러터는 git 사용하는데, XCode 설치하면 같이 따라옴

## 2. Rosetta 설치

애플 실리콘 맥을 사용하는 사람 설치

- 맥애플 실리콘 맥 사용하는지 확인하는 방법

    : 화면의 좌측 최상단 사과 눌러서 about this mac → chip 에 m1, m2, m3 등 m이 적혀있는 무언가가 있다면 애플 실리콘을 사용한다는 뜻 (i7, i9 등이 적혀있다면 intel 칩 사용자)

- 플러터 docs에서 Software requirements 코드 복사 및 터미널 입력

```dart
sudo softwareupdate --install-rosetta --agree-to-license
```

** Rosetta 설치 이유 : Apple Silicon 칩 (예: M1, M1 Pro, M1 Max, M2 등)과 호환되지 않는 Intel 기반 애플리케이션을 실행할 수 있도록 돕는 번역 레이어

## 3. Homebrew 설치

맥에서 개발 할 때에는 거의 필수적으로 설치함.

** 이유 : Homebrew는 다양한 오픈 소스 소프트웨어를 간편하게 설치하고 관리할 수 있는 강력한 도구이므로 특히 개발자에게 유용함

1. [brew.sh](http://brew.sh) 사이트 진입 → ‘Install Homebrew’ 하단의 코드 복사해서 터미널 입력

```dart
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

2. 설치 커맨드 노션으로 들어가서 shell 타입 확인 커맨드 복사 및 터미널 입력

```dart
echo $SHELL
```

3. 출력 값 확인 후 설치 커맨드에서 해당되는 shell 복사 및 터미널 입력
- (/bin/zsh 출력일 때)

```dart
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> $HOME/.zshrc
eval "$(/opt/homebrew/bin/brew shellenv)"
```

- (/bin/bash 출력일 때)

```dart
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> $HOME/.bashrc
eval "$(/opt/homebrew/bin/brew shellenv)"
```

4. 설치된 버전 확인

```dart
brew --version
```

## 4. Flutter SDK 설치

1. 방법 1 - brew로 설치하기

```dart
brew install --cask flutter
```

설치 후 flutter doctor 입력하여 체크표시 여부 확인. (체크 안된 부분은 하단에 따로 설명)

<br>

2. 방법 2 - 직접 설치하기(brew로 설치 실패 시)
    
    1) flutter docs 의 설치 가이드 페이지에서 Get the Flutter SDK 링크에서 본인의 칩에 맞게 zip파일 다운
    

        **이때 내 문서에 다운(또는 바탕화면) ←권한이 필요한 폴더에 설치해서 flutter SDK가 사용할 수 없는 상태가 되는 경우가 많기 때문

    2) 압축 풀기

    3) 터미널에 /bin/zsh 쓰고 있다면 

    ```dart
    vi ~/.zshrc
    ```

    또는 /bin/bash 쓰고 있다면

    ```dart
    vi ~/.bashrc
    ```

    4) 영어 키보드 o 누르고(터미널에서 타이핑 가능) 설치 커맨드 노션의 ‘환경변수 추가 코드’ 복사 및 입력

    ```dart
    export PATH="$PATH:$HOME/Documents/flutter/bin"  //Flutter SDK 설치한 경로
    ```

    5) 터미널에서 esc 눌러 나간 후, :wq 입력 후 엔터 

    6) 터미널 끈 후 다시 열어서 flutter doctor 입력

## 5. XCode 설치

앱스토어에서 XCode 다운로드

1. 설치 커맨드의 ‘MacOS XCode 설치 커맨드’ 복사 및 입력

```dart
sudo xcode-select --install
sudo xcode-select -s /Applications/Xcode.app/Contents/Developer
sudo xcodebuild -runFirstLaunch
```

2. XCode 앱 열어서 상단 Window 탭 → Devices and Simulators 클릭
    
    만약 simulators 탭에 아이폰이 존재하지 않는다면 하단의 + 눌러 OS Version 에서 Download more simulator runtimes… 클릭 → iOS 버전, iOS Simulator 우측의 GET 눌러서 ios runtime들을 설치
    
    (iOS Simulator 없다면 설치 안해도 됨)
    

## 6. Android Studio 설치

1. 구글에 android studio 검색해서 Download Now 페이지 접속 → 메인의 다운로드 눌러서 해당되는 칩에 맞게 다운로드 진행

2. 다운로드 된 dmg 파일 클릭 → android studio를 Applications에 드래그 앤 드랍

3. android studio 열어서 기본 설치 마친 후 plugins 클릭 → Marketplace 탭에 dart. flutter 검색하여 설치

4. android studio 닫았다가 재실행하면 메인에 New Flutter Project 버튼 생성된것 확인 가능

5. 중앙의 More Actions → SDK Manager 클릭 → Android SDK → Android SDK Location에 경로가 비어있다면 Edit 클릭 → Android SDK, Android SDK Platform 체크 후 설치
    
    ** 3번 과정에서 앱을 재실행 했을때부터 설치가 나와서 설치하였던 것과 같은 것 같음!
    
6. 경로 입력된 거 확인 후 하단 SDK Platforms에서 Android API 35 설치

7. SDK Tools 탭에서 Android SDK Build-Tools 35, Android SDK Command-line Tools, Android Emulator, Android SDK Platform-Tools, NDK 체크 후 Apply
    
    ** intel 칩 사용하자라면 intel x86 Emulator Accelerator 도 체크
    
8. Android SDK Location의 경로 전체 복사 → 터미널 열어서 vi ~/.zxhrc 입력 후 엔터 → j눌러서 최하단 내려간 후 o 누르고 하단 내용 입력 → esc 누르고 :wq 입력 후 엔터
    
    ```dart
    export ANDROID_HOME=/Users/jeonhyewon/Library/Android/sdk
    ```
    
9. flutter doctor 입력해서 체크 현황 확인
    
10. 에러 해결
    - Android toolchain 에러
        
        : 터미널에서 flutter doctor - -android-licenses 엔터 → Accept? 뜨면 Y
        
    - CocoaPods not installed 에러
        
        : 홈브루로 cocoapods 설치
        
        ```dart
        brew install cocoapods
        ```
        

## 7. Android Emulator 세팅

1. android studio 홈에서 New Flutter Project 클릭 → Generators에 Flutter 눌렀을때 SDK path가 비어있다면 경로 입력 후 next
    
    ** 경로 확인 : 터미널에서 flutter doctor -v 입력 후 상단에 나오는 경로 복붙
    
2. Project location 우측 … 눌러서 바탕화면에 ‘test_proj’ 이름으로 새 폴더를 만들어서 open

3. 프로젝트 열리면 우측의 Device Manager 클릭(상단 Tools 탭에도 있음) → Create Device에서 아무 Pixel phone 선택(Play Store 란에 마크가 있는걸로 선택) → next 누르고 API35 다운 → AVD Name을 ‘Flutter Inflearn’ 으로 변경(앞으로 사용할 에뮬레이터 이름) → Portrait 선택 →  Show Advanced Settings → 하단 Internal Storage  8GB로 변경하고 끝내면 device manager에 flutter inflearn 에뮬레이터 생성된것 확인 가능

4. 최상단 Android Studio 클릭 후 Settings → 검색창에 emulator 검색 → Launch in a tool window 체크 해제(체크가 되어있으면 방해되는 요소가 꽤 있을 수 있어 원활한 강의 진행을 위함)

5. device manager의 flutter inflearn 우측 재생버튼 클릭 → 에뮬레이터 실행되고, 우측의 … 눌러서 Settings → Emulator always on top 활성화하면 다른 창을 눌러도 항상 보이기 때문에 추천

6. 상단 기기모양에 flutter inflearn 선택하고 재생버튼(run 버튼) 누르면 flutter inflearn이라는 에뮬레이터에서 플러터 코드를 실행하겠다는 뜻(처음 세팅때에만 시간이 다소 걸림) → 앱이 뜨고 하단 + 누르면 숫자가 올라가는것까지 확인하면 안드로이드 에뮬레이터 세팅 끝

## 8. iOS Simulator 설정

1. 안드로이드 스튜디오 상단 모바일 기기 탭에서 Open iOS Simulator 클릭하면 바로 뜸

** 맥에서는 강의할 때 ios 시뮬레이터가 빠르기 때문에 웬만하면 ios 시뮬레이터를 보며 작업하는게 좋음

만약 시뮬레이터가 뜨지 않고 최상단에 글자만 떠있다면 file → open simulator 에서 ios 최신 버전 과 iphone 아무 디바이스 선택하면 시뮬레이터 뜸

1. ios 시뮬레이터 항상 위에 두는 방법 : 시뮬레이터 누르고 최상단 window → Stay On Top 
2. ios 시뮬레이터에서 플러터 앱 실행하는 방법 : 안드로이드 에뮬레이터와 마찬가지로 상단 디바이스 선택하는 탭에서 실행한 아이폰 버전 선택 후 재생버튼 클릭

    ** 프로젝트가 icloud랑 동기화 되어 있으면 파일이 실제 로컬에 존재하지 않기 때문에 동기화 끄고 해야 함