# QT Installer Framework 로 Installer 빌드하기

QT Installer Framework를 설치하면 해당위치에 5개정도의 바이너리가 설치된다.   
이중 패키징에 필요한 파일은 아래와 같다.

- binarycreator
- installerbase
패키징할 폴더 구성은 아래와 같다. (QT Installer Framework 설치 시 example 폴더도 설치되니 참고)
```
config/
  ├─config.xml
  ├─controller.qs // installer UI 또는 특정 부분과 상호 작용하는 기능을 제어하는 스크립트 
packages/
  │ ├─component1/
  │ │ ├─data/ // 실제로 installer를 통하여 설치되어야할 파일들을 위치시킴
  │ │ ├─meta/
  │ │ │ ├─package.xml
  │ │ │ ├─component.qs // installer UI를 추가 삭제하거나 커스텀 페이지를 추가하는 스크립트
binarycreator // installer 생성시 사용하는 바이너리
installerbase // binarycreator 사용 시 필요
```

## Build 명령
```
./binarycreator --offline-only -c config/config.xml -p packages <installer-name>.run
```
