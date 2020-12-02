---
title: "docker rm `docker ps -a -q` 가 모든 컨테이너를 삭제하는 이유"
date: 2020-12-01T10:23:27+09:00
draft: false
---


# 컨테이너를 삭제하려면 ??
컨테이너 삭제
``` shell script
docker rm <container>
```

모든 컨테이너 삭제

``` shell script
docker rm `docker ps -a -q`
```
![picture 1](../../images/5948ab829b2629d79a665f3207094b47ab6b6eb1845855408034caf84f7436d7.png)  




docker rm은 알겠는데 `docker ps -a -q`는 뭘까요??

뒷 부분의 `은 따옴표가 아닌 백틱(backtick)이라고 부르는 기호입니다.
  
보통 키보드의 esc 바로 아래에 있습니다.

# 백틱 (backtick)

백틱의 역할은 명령어를 실행하고 출력을 가져오는 역할입니다.
다시 말해서 docker ps -a -q 명령어를 실행하고 나오는 출력을 docker rm 으로 실행하는거죠.

자... 그럼 docker ps -a -q 만 실행해보겠습니다.

![](.my-first-post_images/945d001a.jpeg)

대강 추측하기로는 컨테이너들의 ID만 출력하는 명령어 같습니다.
공식문서의 ps 부분을 참조하겠습니다.

![](../../static/34654c1b.png)
'docker ps'에 대한 도커 공식문서
`docker ps -a -q` 중 -a 는 모든 컨테이너를 표시하는 옵션이네요.  

디폴트 옵션은 현재 실행 중인 컨테이너만 가져옵니다.

-q 옵션은 ID들만 출력하는 옵션입니다.


## backtick 

docker ps -a -q 는 "모든 컨테이너의 ID만 출력"하는 명령어라고 할 수 있습니다.

```
docker rm `docker ps -a -q` 
```

<모든 컨테이너 ID 나열>
처음에는 어떤 명령어인지 알 수 없던 명령어가 이제는 그렇게 동작하는게 당연하게 느껴지네요.