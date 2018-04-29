# \[도커\] 도커 파헤치기 step2. Webapps with Docker-1

**해당 글은 **[**https://github.com/docker/labs/blob/master/beginner/chapters/webapps.md**](https://github.com/docker/labs/blob/master/beginner/chapters/webapps.md)** 에서 번역 및 의역을 한 것이므로 정확한 것은 명시한 주소에서 확인할 수 있습니다.**

**해당 실습은 단계별로 나눠서 글을 포스팅 합니다.**  


### 서론 {#서론}

step1에서 Running your first container에서 docker run, 도커 주요 용어에 대해서 알아 보았다.  
이번 step2에서는 도커 애플리케이션을 배포하는 것을 다룬다.

### 컨테이너에서 스테틱한 웹사이트를 실행하자. {#컨테이너에서-스테틱한-웹사이트를-실행하자}

[https://github.com/docker/labs/tree/master/beginner/static-site](https://github.com/docker/labs/tree/master/beginner/static-site) 에서 해당 글에 해당하는 코드를 다룹니다.  
첫번째로, 우리는 컨테이너에서 정적인 웹사이트를 실행하기 위해 도커를 사용합니다. 해당 웹사이트는 존재하고 있는 이미지를 토대로 합니다.

그 이미지는 Docker Store에서 찾을 수 있으며, 간단히 single-page 웹사이트 데모를 위해 이미 만들어진 dockersamples/static-site이다.\([https://store.docker.com/community/images/dockersamples/static-site](https://store.docker.com/community/images/dockersamples/static-site)\)

> $ docker run -d dockersamples/static-site

위의 명령어를 실행하여 이미지를 내려 받습니다.  
“이 이미지의 최근 버젼은 -d 플래그가 없이 이미지가 실행되지 않습니다. -d 플래그는 detached mode를 가능하게 해줍니다.  
\(detached mode는 터미널/쉘로 부터 컨테이너를 실행시키는 것을 detach하고, 컨테이너 시작 이후에 명령어를 리턴해줍니다.\)  
보통 이미지의 문제들은 디버깅을 하고 있지만, 지금은 첫번째 예제에 사용하기 위해 -d 를 사용합니다.”

그래서 이 명령어를 실행하면 어떤 일이 일어날까?

도커 호스트에 이미지가 존재하지 않기 때문에 도커 데몬은 레지스트리로 부터 첫번째로 fetch를 한다. 그리고 컨테이너로 이미지를 실행시킵니다.

서버는 실행이되고 있고, 웹사이트를 볼 수 있을까? 무슨 포트가 실행이 되고 있는 중인가요? 그리고 좀 더 중요하게, 어떻게 우리들의 호스트 머신으로 부터 직접적으로 컨테이너에 접근을 할까?

실질적으로, 아직 이 질문에 답변을 할 수 없을 것이다. 이 케이스에서 클라이언트는 어느 포트에서 publish되기 위한 도커 엔진인지 알 수 없다. 그래서 docker run 명령어를 다시 재실행하는 것이 필요합니다.

재실행 하여 publish할 포트와 화면에 보여질 컨테이너의 이름을 커스텀마이징 하여봅시다.  
detached mode을 해당 컨테이너에서 -d 옵션을 다시 사용할 것입니다.

첫번째, 실행되어져 있는 컨테이너를 멈춰야한다. 그러기 위해서는 컨테이너 아이디가 필요합니다.  
detached mode에서 컨테이너는 실행되어져있기 때문에 우리는 이를 위해 다른 터미널을 실행할 필요가 없습니다.  
docker ps를 통해 실행되어져 있는 컨테이너를 확인합니다.

> $ docker ps

CONTAINER ID컬럼에서 체크아웃을 합니다.  
우리는 CONTAINER ID값을 필요로 합니다. 여기서 CONTAINER ID는 긴 문자열의 시퀀스이고, 원하는 컨테이너를 멈추고나서 지우려고 하는 값입니다. 아레의 예는 시스템에서 CONTAINER ID을 제공합니다.  
터미널에서 보는 이 값을 사용해야한다.

> $ docker stop 멈추려고 하는 CONTAINER ID  
> $ docker rm 지우려고 하는 CONTAINER ID

“좋은 기능은 전체에 CONTAINER ID을 쓸 필요가 없다는 것입니다.  
시작하는 문자열의 몇 글자를 입력할 수 있고, 실행 되어진 컨테이너들 중만약 모든 컨테이너들 중에 유니크 하다면, 도커 클라이언트는 똑똑하게 그것을 집어낸다.”  
ex\) CONTAINER ID가 35a9d35beb20라면  
docker stop 35a  
…

아래의 명령어처럼 deched mode에서 컨테이너를 실행시켜보자.

> $ docker run –name static-site-sample -e AUTHOR=”scarlett.kim” -d -P dockersamples/static-site

위의 명령어에서  
-d : 터미널로 부터 detach되어진 프로세스와 함께 컨테이너를 만드는 것.  
-P : 노출된 모든 컨테이너 포트를 도커 호스트의 임의의 포트에 publish함.  
-e : 컨테이너에 다양한 환경을 pass 하는 것.  
–name : 컨테이너 이름을 지정하는 것.  
-AUTHOR : 환경 변수이름이고 Your Name은 이름pass할수 있는 값이다. \(작성자 느낌…\)  
docker port명령어를 실행시켜서 port를 볼 수 있습니다.

> $ docker port static-site-sample \(–name로 지정한 컨테이너 이름\)

맥용 도커, 윈도우용 도커 또는 리눅스에서 실행시키면,  
[http://localhost:\[YOUR\_PORT\_FOR](http://localhost:[YOUR_PORT_FOR/) 80/tcp\] 을 열 수 있습니다.  
예는 [http://localhost:32773](http://localhost:32773/)

만약 맥 또는 윈도우를 통해서 도커를 사용한다면, docker-machine을 명령어를 사용하여 호스트 네임을 찾을 수 있습니다. \(default 머신을 사용하는 것으로 추측하고 있는중…\)

> $ docker-machine ip default
>
> 참고 \) 만약 ‘Error getting IP address: Host is not running’ 에러를 만났다면,
>
> $ docker-machine rm default
>
> $ docker-machine create –driver virtualbox default  
> \(Downloading /Users/블라블라/.docker/machine/cache/boot2docker.iso from [https://github.com/boot2docker/boot2docker/releases/download/v17.12.1-ce/boot2docker.iso...에서](https://github.com/boot2docker/boot2docker/releases/download/v17.12.1-ce/boot2docker.iso...%EC%97%90%EC%84%9C) 멈추고 … 느리더라도 … 인내하고 기다리자…에러가 아니….옵…니다\)  
> 명령어를 실행하여 해결합니다.
>
> Docker Machine 관련 링크
>
> * Docker Machine을 이용하여 Mac에서 docker 운영하기 : [http://blog.saltfactory.net/running-docker-on-mac-using-with-docker-machine/](http://blog.saltfactory.net/running-docker-on-mac-using-with-docker-machine/)\)

http://:\[YOUR\_PORT\_FOR 80/tcp\] 입력하면 사이트를 볼 수 있습니다.  
예를 들어서 , [http://192.168.99.100:32773](http://192.168.99.100:32773/)

> 참고 \) docker-machine ip default에서 나온 아이피로 실행했을 때 안되서 찾아본 링크  
> [http://bluese05.tistory.com/15?category=559611](http://bluese05.tistory.com/15?category=559611)
>
> 만약 안된다면, eval “$\(docker-machine env default\)” 명령어 실행 후  
> 컨테이너, 이미지 다시 실행.  
> $ docker run –name static-site-sample -e AUTHOR=”scarlett.kim” -d -P dockersamples/static-site  
> \([http://docker-k8s-lab.readthedocs.io/en/latest/docker/docker-machine.html](http://docker-k8s-lab.readthedocs.io/en/latest/docker/docker-machine.html)\)

같은 시간에 두번째 웹서버를 실행시킬 수 있다. 컨테이너의 웹서버에 커스텀 호스트 포트 번호를 정의할 수 있습니다.

> $ docker run –name static-site-2 -e AUTHOR=”Your Name” -d -p 8888:80 dockersamples/static-site

실제 서버에 이를 배포하기 위해서는 우리는 도커 인스톨 그리고 docker\(환경 변수로 passed된 도커의 AUTHER을 볼 수 있다.\) 명령어 위에서 실행시키는 것이 필요합니다.

지금 도커 컨테이너안에서 웹서버를 실행시키는 방법은 ? 도커이미지를 어떻게 자신의 것으로 생성하는가?  
다음 주제에서 다루지만, 먼저 사용하지 않는 컨테이너들을 모두 멈추고 지워야합니다.

### 도커이미지 {#도커이미지}

이 부분에서는 도커이미지에 대해 깊게 파고 들려고 합니다. 이미지를 만들고 해당 이미지를 사용하여 로컬에서 응옹프로그램을 실행하고 마지막으로 일부 이미지를 도커 클라우드로 푸시 할 것입니다.  
도커 이미지는 컨테이너를 기반으로 하고 있습니다. 이전 예제에서는 레지스트리에서 dockersamples/static-site 이미지를 꺼내 도커 클라이언트에게 해당 이미지를 기반으로 컨테이너를 실행하도록 요청 했습니다.

시스템의 로컬에 사용가능한 이미지들을 보기 위해 docker images 명령어를 실행합니다.

> $ docker images

TAG 컬럼은 이미지의 특정 스냅샷을 말하며, ID\(IMAGE ID\)는 해당 이미지에 해당하는 고유 식별자 입니다.

간단히 설명하면 깃 저장소의 이미지로 생각할 수 있습니다. \(이미지는 변경된 것들을 커밋할 수 있고, 다양한 버젼을 가집니다\) 특별한 버젼 넘버를 제공하지 않는다면, 클라이언트는 latest가 기본값입니다.

예를 들어 ubuntu이미지의 특정 버젼을 내려 받을 수 있습니다.

> $ docker pull ubuntu:12.04

이미지의 버젼 정보를 지정하지 않으면 도커 클라이언트는 기본값으로 latest로 지정이 됩니다.  
예를 들어 아래 docker pull명령어는 ubunto:latest의 이미지를 가져 옵니다.

> $ docker pull ubuntu

새로운 도커 이미지를 가져오기 위해 레지스트리로부터\(도커 스토어와 같은\) 이미지를 얻거나 자신의 이미지를 만들 수 있습니다.

도커 스토어에는 사용가능한 이미지들이 수 십 만개의 이미지가 있습니다.

docker search라는 명령어를 통해 직접적으로 이미지들을 찾을수 있습니다.

이미지아 관련하여 중요한 차이점은 base image와 child image이다.

Base image는 parent 이미지를 가지지 않고, 일반적으로 ubuntu, apline 또는 debian과 같은 OS가 있는 이미지입니다.

Child image는 base image을 구축하고 추가적인 기능을 기반으로 추가하는 이미지 입니다.

또 다른 핵심 개념은 Official image와 User image입니다. \(둘다 base image 이거나 child images입니다\)

Official image는 도커가 승인한 이미지 입니다. Docker, Inc는 모든 공식 리포지토리 콘텐츠를 검토하고 게시하는 전용 팀을 후원 합니다. 이 팀은 업스트림 소프트웨어 관리자, 보안 전문가 및 광범위한 Docker 커뮤니티와 협력합니다. 이러한 이름 앞에는 조직 또는 사용자 이름이 붙지 않습니다.

위의 이미지 목록에서 파이썬, 노드, alpine, nginx 이미지는 공식 \(기본\) 이미지 입니다.

훨씬 더 자세한 내용은 [https://docs.docker.com/docker-hub/official\_repos/](https://docs.docker.com/docker-hub/official_repos/) 에서 확일할 수 있습니다.

User image는 사용자가 만들고 공유하는 이미지 입니다. base images를 구축하고 추가적인 기능을 기반으로 추가하는 이미지 입니다. 일반적으로 이들은 user/image-name형태를 가집니다. user값은 도커스토어 user 이름 이거나 조직 이름의 값입니다.

