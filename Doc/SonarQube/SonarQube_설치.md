# SonarQube 설치

## SonarQube란?
소나큐브는 20개 이상의 프로그래밍 언어에서 버그, 코드 스멜, 보안 취약점을 발견할 목적으로 정적 코드 분석으로 자동 리뷰를 수행하기 위한 지속적인 코드 품질 검사용 오픈 소스 플랫폼이다.  
[공식 Document](https://docs.sonarqube.org/latest/)  
[CURVC의 SonarQube 컨플런스](https://confluence.curvc.com/display/ASD/SonarSource+Product)

## OpenJDK 설치
SonarQube는 JDK 11 버전이상이 설치되어 있어야한다.  
Oracle JDK는 라이센스 문제가 있을수 있으므로 OpenJDK를 설치한다.  
https://recipes4dev.tistory.com/173

## SonarQube 설치
아래 링크에서 zip파일을 다운받은 뒤 압축해제  
bin/ 경로에는 각 OS별 바이너리가 있으며 OS에 맞게 실행  
https://www.sonarqube.org/downloads/

### Windows
```
$ StartSonar.bat
```
### Linux & macOS
```
$ ./sonar.sh start
```
기본적으로 **localhost:9000**으로 동작  
계정은 **admin/admin**
> SonarQube 실행 후 동작까지 어느정도 시간이 소요됨

## SonarQube 서비스 등록
(서비스 등록은 Windows만 설명하겠음)  
설치한 SonarQube의 바이너리를 보면 아래와 같은 파일이 있다.  
각 파일들을 관리자 권한으로 실행한다.
- InstallNTService.bat
- StartNTService.bat
실행 후 아래와 같이 서비스가 추가된 것을 확인할 수 있다.
![](./images/service.png)

## 참고 문서
[서비스 등록](http://pseg.or.kr/pseg/infouse/5003)
