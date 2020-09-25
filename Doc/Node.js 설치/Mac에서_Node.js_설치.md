# Mac에서_Node.js_설치
Mac에서 Node.js를 설치하는 방법은 대표적으로 3가지가 있다.

- 공식사이트에서 배포하는 .pkg파일을 통하여 설치
- nvm으로 설치
- homebrew (권장)

## 공식사이트에서 다운받아 설치 
1. https://nodejs.org 에서 .pkg파일을 받아 설치

2. /usr/local/bin에 node 와 npm 바이너리가 각각 복사되고 환경변수에 추가됨

 - 이 방법으로 설치하면 npm install 마다 sudo 권한이 항상 필요

## nvm 으로 설치 시도
1. nvm 설치 시도
```
$ curl https://raw.githubusercontent.com/creationix/nvm/v0.30.2/install.sh | bash
```

2. 원하는 버전의 node 설치
```
$ nvm install v8.17.0
```

3. 설치한 node 리스트 보기
```
$ nvm list
```

4. 설치한 node 사용 (이방법은 해당 터미널에서만 적용됨 글로벌하게 사용 불가능)
```
$ nvm use 8.17.0
```

5. 디폴트로 사용할 노드 적용 (글로벌하게 사용 가능)
```
$ nvm alias default 8.17.0
$ nvm use default
```

## Homebrew로 설치
Homebrew란 Mac OS의 패키지 관리자이다.

Homebrew도 brew install node로 바로 설치하면 글로벌 설치 시 sudo 권한이 필요하기 때문에 아래와 같이 npm과 node를 따로 설치해야한다.

(현재 Node.js와 npm을 따로 설치하는 옵션이 사라져 불가능)

1. Homebrew 설치
```
$ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

2. 설치가능한 Node 패키지 확인
```
$ brew search node
```

3. Node.js 설치
```
$ brew install node@8
```

homebrew는 구버전에 대해서는 지원을 잘 하지않아 메이저버전의 최신버전들만 지원함 (작성일자를 기준으로 node@8은 삭제되어 동작하지않음)

만약 node@8이하의 버전을 homebrew를 통하여 설치하려는 경우 아래 링크를 참조

[Mac에서 Node.js 다운그레이드](./Mac에서_Node.js_다운그레이드.md)

3. .npmrc 생성
```
$ echo prefix=~/.npm-packages >> ~/.npmrc
```

4. 환경변수 추가 (심볼릭 링크 생성)
```
$ brew link --overwrite node
```

위 코드가 동작하지 않을 경우 아래와 같이 실행하여 환경변수 등록

```
$ echo 'export PATH="/usr/local/opt/node@8/bin:$PATH"' >> ~/.bash_profile
$ . .bash_profile
```

5. npm 설치
```
$ curl -L https://www.npmjs.com/install.sh | sh
# Permission denined 관련 에러 발생 시
# https://www.npmjs.com에서 직접 install.sh를 다운받아 755권한을 주고 실행한다.
```

6. npm-packages 환경변수 추가
```
$ echo 'export PATH="$HOME/.npm-packages/bin:$PATH"' >> ~/.bash_profile
$ . .bash_profile
```

## 환경변수 확인
```
echo $PATH
```

## 시스템 서비스로 환경변수 추가
launchctl 를 사용하여 macOS의 서비스로 환경변수를 등록
```
$ sudo launchctl config user path $PATH # 이 후 재부팅 필요
$ reboot
```
[GUI 프로그램이 환경변수를 찾지 못할 경우 - macOS]()

## 참고문서
[homebrew로 nodejs 설치](http://hochulshin.com/node-install-osx/)

[nodejs 삭제](https://gomugom.github.io/how-to-remove-node-from-macos/)

[homebrew 삭제](http://sinius.net/2015/01/01/how-to-uninstall-homebrew/)

[nvm 설치](http://junsikshim.github.io/2016/01/29/Mac%EC%97%90%EC%84%9C-Node.js-%EC%84%A4%EC%B9%98%ED%95%98%EA%B8%B0.html)