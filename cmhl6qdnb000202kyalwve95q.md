---
title: "Comprehensive Guide to Architecture Basics"
datePublished: Tue Nov 04 2025 23:13:27 GMT+0000 (Coordinated Universal Time)
cuid: cmhl6qdnb000202kyalwve95q
slug: comprehensive-guide-to-architecture-basics

---

cloud bus

* 중앙에서 config서버 변경시 재시동해야하지만, 클라우드 버스를 이용하면 mq(massage queue)를 사용해 재시동하지 않고도 클라이언트 서버들에게 변경 사항을 배포할 수 있다.
    

Fargate

* EC2의 서버리스 버전이라고 생각하면 편하다. 사용자가 직접 서버를 구축하지 않고도 컨테이너를 실행할 수 있도록 해준다. 이후 ECS나 EKS같은 오케스트레이션 툴로 관리한다.
    

서버리스

* 서버리스 방식은 사용자가 서버를 직접 구축하지 않고 공급자가 서버를 책임지고 있다. 따라서, 트래픽에 따른 서버 자동 확장이나 유지 보수에 힘들이지 않고 원하는 코드를 실행시킬 수 있다.
    

Lambda

* 서버를 구축하지 않고도 함수를 자동으로 실행시킨다. 함수를 실행시켜달라는 요청이 올 때만 서버를 키고 끄기에 비용을 절약할 수 있지만, 서버가 꺼져있는 상태에서 요청이 오면 재시동 시간과 함수를 처리하는 시간까지 더해져 콜드 스타트(딜레이)가 있을 수 있다.
    

Mongo DB

* 몽고DB는 NoSql의 대표격이다. 이것을 사용하는 이유는 여러가지로 나뉠 수 있다. Reliablity, Scalability, Flexibility, Index 등이 있다.
    
    * Reliablity
        
        * 첫째는 신뢰성인데, 각 레플리카 셋에서 관리하는 DB들의 장애 복구를 빠르게 처리할 수 있다. Primary 서버가 각 secondary 서버들을 관리하고 모니터링하며, 장애 발생시 빠르게 복구시킨다. 또한, Primary 서버가 다운되면, Secondary 서버 중 하나가 Primary 서버가 되어 장애를 복구한다.
            
    * Scalability
        
        * 둘째는 확장성이다. 데이터가 많아질 경우 자동으로 스케일 아웃을 하여 서버의 수를 늘린다. 또한, 기준을 통해서 각 데이터들을 분리한다. 그렇게 나뉘어진 각 데이터 뭉치들을 샤드라고 부른다. 한 샤드에 데이터가 몰릴 때는 기준을 바꿔 한 샤드에 데이터가 몰리지 않도록 분산한다.
            
    * Flexibility
        
        * Mongo DB는 NoSql이기에 비정형 데이터를 저장하는 데이터 베이스이다. 각 테이블에 저장하는 것이 아닌, Json같은 형식의 파일에 데이터를 저장한다. 이에 따른 이점은 어떤 한 테이블에 집어넣을 수 없는 데이터가 필요하다면, 관계형 데이터베이스에서는 행을 계속해서 만들어야 하지만, NoSql에서는 Json 파일에 Key-Value값을 하나 추가하여 간단히 만들 수 있다.
            
    * Index 지원
        
        * MongoDB는 다른 NoSQL과 다르게 Index를 지원한다. 이는 MongoDB의 장점인데, 관계형 데이터 베이스의 경우에는 각 행별로 목차를 정렬하여 원하는 행의 원하는 값을 찾을 수 있다. 그런데, NoSql은 비정형 데이터이기에 원하는 행(테이블)별로 값을 정렬할 수가 없었다. 그러나, MongoDB는 이를 해결한다.
            
    * 또한, 다른 NoSql과 다른 점이 또 있다. 각 로그를 수집한다..??
        

NAT

* Network Address Transition이며, 사설 네트워크안에 있는 서비스들을 NAT를 통해 공인 아이피로 외부 인터넷과 소통할 수 있게끔 한다.
    

MSK

Route 53

웹 소켓

…