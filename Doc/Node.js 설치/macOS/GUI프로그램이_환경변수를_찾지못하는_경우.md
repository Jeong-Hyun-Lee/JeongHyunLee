# Mac에서 GUI 프로그램이 환경변수를 찾지 못하는 경우
## 이슈 사항

GUI 프로그램 실행 시 환경변수를 제대로 찾지못하여 /usr, /bin 및 /usr/local 에 있는 명령들을 사용하지 못하는 이슈

더블클릭하여 실행을 하면 환경변수를 제대로 찾지못함   
터미널을 열어 open 명령으로 실행을 하면 환경변수를 제대로 찾음
## 이슈 원인

OS X 10.11 엘 캐피탄 이상에서 *루트리스(Rootless)라는 보안체계가 새롭게 도입되었다.   
루트리스로 인한 OS X의 이슈라고 한다.

## 이슈 해결

Mac OS의 서비스를 관리하는 launchctl 를 사용하여 환경변수를 등록한다. 아래와 같이 입력한다.   
(launchctl setenv 옵션은 동작하지 않았다.)
```
$ sudo launchctl config user path $PATH
```
이 명령을 실행 후 재부팅이 필요하다.

## 루트리스란?

루트리스란 사용자가 /usr, /bin, /sbin, /System 과 같은 위치의 시스템파일에 수정을 가할수 없도록 차단하는 기능이다.   
(파일 복사, 생성, 삭제, 심볼릭 링크 등 모든 것이 불가능)   
해제 방법은 맥 시동시 Command + R을 눌러 로컬 복구 시스템에서 터미널을 열어 아래와 같이 입력
```
$ csrutil disable
```
상태 확인 방법은 
```
$ csrutil status
```

## 참고문서
[환경변수](https://code.i-harness.com/ko-kr/q/21208)   
[루트리스](http://macnews.tistory.com/3408)