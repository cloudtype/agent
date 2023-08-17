# Cloudtype Agent

클라우드타입 에이전트를 사용하면 사용 중인 쿠버네티스 클러스터를 연결하여 클라우드타입의 기능을 통해 빌드/배포를 수행할 수 있습니다. 이 문서에 따라 에이전트를 쿠버네티스 클러스터에 설치하고 클라우드타입에 연결하세요.



## 도큐멘테이션

자세한 설치 및 설정 가이드가 포함된 문서는 [클라우드타입 Docs](https://docs.cloudtype.io/) 에서 찾을 수 있습니다. (추가 예정)

관련 자료

- [클라우드타입, AWS Elastic Kubernetes Service를 활용한 개발자 플랫폼 구축하기](https://github.com/cloudtype-examples/webinar-03)



## 시작하기

에이전트를 설치하기 위해 다음이 필요합니다.

- 1.22 버전 이상의 쿠버네티스
- 읽기 및 쓰기 권한이 있는 프라이빗 레지스트리
- Ingress 및 Cert Manager
- 기본 스토리지 클래스



1. 다음 명령어를 사용해서 에이전트를 설치하세요.

```sh
$ kubectl apply -f https://raw.githubusercontent.com/cloudtype/agent/master/k8s/agent.yaml
```

2. 에이전트의 접속 주소를 확인합니다.

```sh
$ kubectl get service/agent -n cloudtype -o jsonpath='{.status.loadBalancer.ingress[0].ip}'
```

2. 접속 토큰을 확인합니다.

```sh
$ kubectl get secrets agent-secret -n cloudtype -o jsonpath='{.data.agent-token}' | base64 --decode
```

설치 후 클라우드타입의 클러스터 설정 패널에서 도메인 및 레지스트리 정보를 설정하고 관리할 수 있습니다. 


