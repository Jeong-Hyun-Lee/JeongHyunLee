# Mac에서_Node.js_다운그레이드
Homebrew를 통하여 Nodejs를 다운로드한 경우에만 해당한다.

Homebrew는 최신의 패키지를 유지하며 구 버전의 패키지들에 대해서는 지원을 잘 하지않는다.

## 설치가능한 Node 패키지 확인
```
$ brew search node
```

node 관련 패키지들이 표시되는데 이때 내가 원하는 버전의 node가 없을 수 있음 (node@8을 설치하려는 경우)

이전버전의 node를 설치하기 위하여 homebrew의 git repository에서 node@8을 삭제하기전의 커밋에서

8버전대의 node를 설치할 수 있는 node@8.rb파일을 임시로 가져온다.

## homebrew git repository로 이동
```
$ cd $(brew —repo homebrew/core) # homebrew의 레포로 이동
# homebrew repository에 보면 Formula 디렉토리가 있는데 설치가능한 패키지들을 모아놓음 brew search는 여기있는 패키지들을 검색하는 것으로 보임
```

## node@8이 삭제되기전의 특정 커밋으로 부터 .rb파일을 가져옴
```
$ git checkout d298ead12 Formula/node@8.rb
# d298ead12 는 node@8을 삭제하기전의 커밋이며 이 커밋에서 node@8.rb 파일을 받아온다.
# 보다 이전버전의 node를 받으려면 삭제되기전의 특정 커밋을 찾아야함
```

## node@8 설치
```
$ brew install node@8
```

임시로 가져온 .rb파일 삭제
```
$ rm Formula/node@8.rb
```
