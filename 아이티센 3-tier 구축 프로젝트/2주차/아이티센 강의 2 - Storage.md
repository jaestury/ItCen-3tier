# Storage
 
- 저장소, 저장 공간.

### 네이버의 경우

- Object Storage : 모든 종류의 데이터를 인터넷상에 저장, 검색할 수 있는 스토리지. 객체형태로 저장한다.

- Archive Storage : 데이터 아카이빙 및 장기 백업에 최적화 (Archive : 시간을 들여 무언가를 오랫동안 보관한다. 과거 데이터, 적재 데이터를 보관하기 좋다.)

- Block Storage : 데이터를 블록 단위로 분할, 고유 식별자를 부여하여 저장하는 스토리지. 블록 스토리지와 객체 스토리지는 다르다.

- NAS : 다수의 서버를 네트워크에 연결하여 사용할 수 있는 스토리지

- Backup : 전문 솔루션을 통해 데이터를 임시로 복제하고 보관하는 서비스

### Object Storage

- 버켓 생성

- 인터넷이 연결되어 있는 환경에서 파일을 공유하고 업로드/다운로드할 수 있다. 공개를 안할수도 있다.

- 버켓은 이름이 겹치면 안된다. 네이버 클라우드 안에 같은 이름이 존재해서는 안됨.

- 객체에 접근할 수 있는 권한이 없다면 접근 불가. 권한을 같이 전송해주면 열람이 가능하다.

- 공개로 전환하면 당연히 열람 가능하다.

### 정적 웹 호스팅

- 홈페이지 개설 가능

- HTML 파일만 업로드해도 홈페이지를 생성할 수 있다.

- 폴더 전송은 안된다. 때문에 새 폴더를 생성한 뒤 파일을 넣어주어야 한다.

![image](https://user-images.githubusercontent.com/108641325/193193091-ab3ea624-cb1f-47a0-8fb0-2eb5b922504b.png)
(버켓 -> 정적 웹사이트 호스팅)


![image](https://user-images.githubusercontent.com/108641325/193193103-aadff017-6ba9-4ef5-ae96-7ca8bbbe95be.png)

(정적 웹 호스팅 성공)


- HTML : 홈페이지 생성의 기초. / css : 홈페이지를 예쁘게 해줌

- 404 not found : 파일이 없음

- 403 not found : 권한이 없음

- 활용도가 높지는 않았지만, 요새는 많이 사용한다.

- 예전에는 홈페이지에서 모든 서비스와 작업을 수행했음(회원가입, 서비스 이용 등등). 요새는 앱으로 추세가 넘어가면서 홈페이지의 역할이 많이 축소되었다.

- 웹 홈페이지는 단순한 홍보와 작업 내용을 출력하는 정도로 간소화되었다. DB를 연결하고 데이터를 불러오고 다시 넘기는 등의 일련의 일을 할 필요가 없어졌고, 정적 호스팅도 많이 사용처가 높아졌다.

- 리눅스 기반 OS에서는 '확장자'라는 개념보다는 파일이름이라는 느낌으로 이해하면 편하다.

### Block Storage

- Server 탭에서 생성해야하고, 자신의 서버에 매칭되게 된다.


![image](https://user-images.githubusercontent.com/108641325/193193126-2adf9a13-d2d8-495e-ac6e-97fe63daa080.png)
(매칭됐다.)

- HDD와 SSD의 고민.
   
   - SSD는 굉장히 빠르다.
   - HDD도 근데 나름 빠름. 못쓸정도는 아님.
   - HDD의 장점 : 저렴한 가격에 대용량을 지원받을 수 있다.

   - 내가 하고자 하는 서비스가 성능이 중요한가? = SSD
   - 성능보다 용량의 중요도가 더 높은가? = HDD
   - 아카이브 스토리지에는 HDD가 더 적합하다. 많이 사용하지 않는 데이터를 적재해야하는 것이기 때문에 많은 용량이 필요하고, 성능이 엄청나게 좋을 이유가 없으며 저렴한 스토리지가 필요하다.


![image](https://user-images.githubusercontent.com/108641325/193193153-71d17c11-1326-49e8-8ef9-7571e6b06fa5.png)
(블록 스토리지를 무제한으로 생성할 수 있는 것은 아니다. 리눅스 서버에는 스토리지 15개를 추가할 수 있다.)


### 파일 시스템

- 윈도우의 파일 시스템은 NTFS

![image](https://user-images.githubusercontent.com/108641325/193193184-a13d5c6b-1f06-416c-9621-a7be1ebdc376.png)

- 블록 시스템은 파일 시스템으로 포맷팅해서 사용한다.

- UUID를 활용하는 것이 좋다.

- 리눅스에서는 접속 'mount'가 자동으로 되지 않는다. 때문에 수동으로 연결해주어야 한다. 항상 해주는 것이 귀찮다면, 그리고 매번 필요하다면 /fstab을 수정해서 추가해주면 좋다.

### FTP

- 파일질라, 알FTP

> sftp ncloud@(공인IP)

---

# Networking

### Load Balancer

- 부하분산 기능. 갑작스런 트래픽 증가등으로 인해 부하가 발생하면 서버, 웹 서비스 등의 프로세스가 죽는다. 그럴 경우 프로세스를 다시 실행해야하고 OS를 재실행해야한다.

- 해결 방법

  1. Scale Up : 스펙을 올림. 직관적이지만, 한계가 존재한다.
  2. Scale Out : 서버를 하나 더 사서 둘을 고르게 사용한다.
	 1) 고정 IP 하나씩 사용하기 : 부하 분산을 할 수는 있지만, 잘 안될 가능성이 있다. A서버의 이용자였는데 B서버로 이동하게 된다면 A서버에서 하던 작업내용을 잃어버릴 수 있다. 세션이 유지되지 않기 때문.
	 2) 로드 밸런서 사용하기 :
	 
	 ![image](https://user-images.githubusercontent.com/108641325/193193215-ff89ca4c-1ec0-46f5-bee7-f6b62397dacc.png)
	 
	 ![image](https://user-images.githubusercontent.com/108641325/193193235-dff2c60d-57b0-4004-b701-a4e368ee1fce.png)
	 
	 ![image](https://user-images.githubusercontent.com/108641325/193193244-6b915e40-1fbb-43d6-a8b7-7afbe0c2d119.png)

	 
	 - 로드밸런서를 사용한다면, 굳이 공인 IP를 사용할 필요가 없다. 로드밸런서는 비공인 IP로 접속을 하기 때문.
	 

### SSL VPN, IPsec VPN

- 보안과 밀접한 연관이 있다. 비공인 IP는 네이버 클라우드 안에서만 사용 가능. 사설망에서만 사용 가능하고, 여기를 넘어가면 없는 IP이다.

- 사설망을 사용하는 방법이 두가지.

- 쓰임새가 완전히 다르다. 10 대역에 접속하기 위해서는 VPN을 사용해야함.

- 보안을 통해 데이터가 안전히 보호된다.

- SSL VPN: 기계가 나만 있어도 됨. EX) 공유기

- IPsec VPN: 나도 하나, 너도 하나 있어야 됨. 상호 연결을 위해 양쪽 다 기계가 필요하다.

### Nat Gateway

- 사설망은 대역이 정해져있다. 사설망 대역에 있는 것들은 가상 IP이기 때문에, 밖에서 이것을 이용해서 상대 컴퓨터에 접속할 수 없다(같은 사설망이라면 가능).

- 사설망은 인터넷 접속을 못 한다. 원래라면 사설망을 사용해서는 인터넷을 사용할 수 없다. 사설망은 외부 인터넷과 통신이 안된다.

- NAT를 사용하면 이것이 가능하다! NAT는 사설 IP를 공인 IP로 변환시켜준다.

---

# Database

- 한개의 서버에서 모든 것을 다 하는 것 : 1-tier

- 보통은 3티어정도로 사용한다.

- Master와 Standby Master
   
   - 1-tier일 때 서버가 꺼지면 걍 다 죽는다.
   - 때문에 똑같은 서버를 만들어두고 만약에 대비하는 것. 혹시 죽을지도 모르는 순간이 올 수 있다.

- 이중화를 통해 가용성을 높여준다.

- DB서버 생성할 때 한개만 만드는 것도 가능하나, 위험하다. 혹시라도 죽으면, 시스템 전체가 다운되기 때문. 비용을 아껴도 되는 서비스인지, 가용성이 더 중요한 서비스인지 고민이 필요하다.

- 하나만 만드는 것은 Stand Alone

- 네트워크에 문제가 생겼다면 방화벽을 사용하자. 

- 3306 : MySQL이 사용하는 포트.

- 이렇게 만들어진 서비스는 2-tier
