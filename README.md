# 🔑 About

https://github.com/gkqkehs7/egusajo-Backend/assets/77993709/9ae0bde0-dd8b-4d08-a741-dce171a3d8d6

생일 펀딩해주는 앱 어플리케이션 입니다.
 
<br />

# 📎 Souce Code 
https://github.com/inha-commit/egusajo-nest
 
<br/>

# ⚒️ Project Architecture

<img src="https://github.com/gkqkehs7/egusajo-Backend/assets/77993709/64008bd3-870f-4361-99cc-b56ab18dcca5" />

<br/>

## 🔍 Nest.js(v9.0.0) Request Pipeline

<img src="https://github.com/gkqkehs7/egusajo-Backend/assets/77993709/aa0af3be-385c-4045-93d5-e27a4d5eb573" />

<br/>

### ****Joi를 이용한 환경변수 유효성 검사****

`Joi` 라이브러리를 이용하여 환경변수에 대한 유효성과 타입을 검사하여 런타임 에러를 방지하였습니다.

<br/>

### **Guard를 이용한 유저 유효성 검사**

Guard를 이용하여 request의 header를 체크하여 유저 유효성을 검사하였습니다.

<br/>

### **Winston.js를 통한 로그 기록**

nest.js의 내장로거를 `Winston.js` 로 대체하여 `info` `warn` `error` level로 나누고 서버에 들어오는 모든 요청, 서버에서 발생하는 모든 에러에 대해 파일로 기록하였습니다.

<br/>

### **Pipe를 이용한 요청 변수 검사**

Validation-pipe를 이용하여 client의 요청을 class-validator로 검사하고, class-transformor로 데이터 변환이 필요한 데이터에 대해 요청을 변환하였습니다.

<br/>

### ModelConvertor로 필요한 데이터만 서비스함수에 전달

Database에서 받아온 데이터를 Convertor로 mapping하여 service로 전달하였습니다.

<br/>

### **ResponseDto로 사용자에게 필요한 데이터만 Re-mapping**

Service에서 return한 데이터를 다시 `ResponseDto` 로 다시 mapping하여 client에게 필요한 데이터만 전송하도록 하였습니다.

<br/>

### **Interceptor를 이용한 http 응답시간 계산**

Interceptor를 이용하여 http 요청에 대한 응답시간을 계산하고 기록하였습니다.

<br/>

### ExceptionFilter를 확장한 Error Filter **Cutsomizing**

nest.js의 `ExceptionFilter` 를 확장하여 서버에서 발생할 수 있는 에러를 `BadRequestError` , `UnauthorizedError` , `ForbiddenError` , `InternalServerError` , `NotFoundError` 로 나누어 class화 하고 Front-end가 처리할 수 있는 에러들에 대해선 ErrorCode들을 미리 enum type으로 정의해 둔 다음, 해당 에러에 맞는 class로 mapping하여 client에게 전송하였습니다.

<br/>

## 🔍 TEST

### Jest를 이용한 유닛 테스트

`Jest` 를 이용해서 controller와 service 함수에 대해 각각 테스트를 진행하였습니다.

[✏️ Jest를 이용한 unit test](https://velog.io/@gkqkehs7/nest.js-tdd-unit-test)

<br/>

### Typeorm-extension을 이용한 데이터 seeding

`typeorm-extension`을 이용하여 `faker.js`로 데이터를 seeding 하고 유저별로 API를 테스트하였습니다.

[✏️ typeorm-extension으로 데이터 seeding하기](https://velog.io/@gkqkehs7/typeorm-extension%EC%9C%BC%EB%A1%9C-%EB%8D%B0%EC%9D%B4%ED%84%B0-seeding)

<br/>

### Artillery를 이용한 부하 테스트

**`Artillery`** 를 이용하여 60초 동안 초당 요청횟수를 늘려가면서 `development` `production` 레벨에서 각가 부하 테스트를 진행하였습니다.

[✏️ Artillery로 서버에 부하테스트 하기](https://velog.io/@gkqkehs7/Artillery%EB%A1%9C-%EC%8A%A4%ED%8A%B8%EB%A0%88%EC%8A%A4-%ED%85%8C%EC%8A%A4%ED%8A%B8-%ED%95%98%EA%B8%B0)

<br/>

### Artillery 테스트 결과로 컨테이너 개수 조절

`Load Balancing` 이 적용되어 있는 실제 서버에 `Artillery` 로 테스트를 진행하여 요청을 받아들일 수 있는 적당한 컨테이너 개수를 선정하였습니다.

[✏️ Artillery 테스트를 통한 실제 서버 컨테이너 개수 조절](https://velog.io/@gkqkehs7/%EC%8B%A4%EC%A0%9C-%EC%84%9C%EB%B2%84%EC%97%90-%EB%B6%80%ED%95%98-%ED%85%8C%EC%8A%A4%ED%8A%B8%ED%95%98%EA%B8%B0)

<br/>

### Artillery 테스트로 메모리 누수 발생 문제 코드 수정

`Artillery` 로 테스트를 진행하며 메모리 누수를 확인하였고, 디버깅하여 메모리 누수 코드를 발견하고 수정하였습니다.

[✏️ Artillery 테스트를 통한 메모리 누수 발생 및 코드 수정](https://velog.io/@gkqkehs7/%EB%B6%80%ED%95%98-%ED%85%8C%EC%8A%A4%ED%8A%B8%EB%A1%9C-%EB%A9%94%EB%AA%A8%EB%A6%AC-%EB%88%84%EC%88%98-%EC%BD%94%EB%93%9C-%EB%B0%9C%EA%B2%AC-%EB%B0%8F-%EC%88%98%EC%A0%95-Eager-Lazy-loading)

<br/>

## 🔍 Github action

### CI

`docker/build-push-action@v4` 를 이용하여 DockerFile에 작성된 대로 우리의 서비스를 이미지로 만들어 `Github packages`에 저장되도록 하였습니다.

<br/>

### CD

`Github packages`에 저장된 이미지를 `appleboy/ssh-action@master` 를 이용하여 우리의 클라우드 서버에 접근하여 이미지를 컨테이너화 하여 서비스를 실행할 수 있게 하였습니다.

[✏️ Github-action을 통한 CI/CD](https://velog.io/@gkqkehs7/Github-action%EC%9D%84-%ED%86%B5%ED%95%9C-CICD)

<br/>

## 🔍 Docker

### Docker-network를 이용한 컨테이너 그룹화

`Docker-network` 를 이용하여 `Server`  `MySQL` `Redis`를 한 network로 묶어 외부에서의 액세스를 제어하고 네트워크 수준에서 보안을 강화하였습니다.

<br/>

### Docker-compose를 이용한 컨테이너 관리

`docker-compose.yml` 파일에 컨테이너를 실행하는데 필요한 네트워크, 볼륨, 환경 변수 등을 정의하여. 가독성이 좋게 하였고, 애플리케이션 구성을 이해하고 공유하기 쉽게 하였습니다.

<br/>

## 🔍 Nginx

### Reverse proxy를 이용한 Https적용

`nginx` 를 이용해 http로 80번 port에 들어온 요청들에 대해서 대리로 받은 다음, 443번 port로 redirect시켜서 보내주고. `리버스 프록시는(reverse-proxy)` 를 이용해 4000번에서 작동하고 있는 node.js서버로 요청이 가게 하였습니다. 이렇게 `리버스 프록시는(reverse-proxy)`를 통해 서버를 감추고, SSL/TLS 암호화를 사용하여 데이터를 안전하게 전송할 수 있게 하였습니다.

[✏️ Http와 Https 그리고 SSL은 각각 무엇일까? |](https://velog.io/@gkqkehs7/HTTP%EC%99%80-HTTPS-%EA%B7%B8%EB%A6%AC%EA%B3%A0-SSL) [✏️ Nginx란 무엇이고 왜 사용할까? |](https://velog.io/@gkqkehs7/nginx-web-server-was) [✏️ Nginx 설치 및 Https 적용하기](https://velog.io/@gkqkehs7/nginx-%EC%84%A4%EC%B9%98-%EB%B0%8F-https-%EC%A0%81%EC%9A%A9)

<br/>

### 하나의 서버로 ****두개의 port에 대해 서로다른 도메인 적용하기****

리눅스 서버에 이미 도메인이 적용되어 있어서 Nginx의 reverse-proxy를 이용하여 하나의 서버에 두개의 도메인이 적용되도록 하였습니다.

[✏️ 두개의 port에 대해 서로다른 도메인 적용하기](https://velog.io/@gkqkehs7/%EB%91%90%EA%B0%9C%EC%9D%98-port%EC%97%90-%EB%8C%80%ED%95%B4-%EC%84%9C%EB%A1%9C%EB%8B%A4%EB%A5%B8-%EB%8F%84%EB%A9%94%EC%9D%B8-%EC%A0%81%EC%9A%A9%ED%95%98%EA%B8%B0)

<br/>

### Docker + Nginx를 이용한 Load Balancing 적용

`docker-compose` 를 이용해 컨테이너 개수를 늘리고 `nginx` 를 이용해 `least_conn` 방식을 이용해 현재 연결 상태를 고려하여 트래픽을 분산시켜 서버 간의 부하를 균등하게 분배하였습니다.

[✏️ Nginx + Docker로 Load Balancing하기](https://velog.io/@gkqkehs7/Nginx-Docker%EB%A1%9C-Load-Balancing%ED%95%98%EA%B8%B0)

<br/>
