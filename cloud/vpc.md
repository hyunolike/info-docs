## `VPC` (추가)`VPN` 
> [참고자료](https://jbhs7014.tistory.com/164)

- `aws` vpc 기준으로 설명!
### `VPC`
> Virtual Private Cloud
- 사용자가 정의하는 가상의 네트워크
- 각 인스턴스가 속하는 네트워크 구분하여 각 네트워크에 맞는 설정 부여 가능


|VPC ⭕|VPC ❌|
|---------|---------|
|![image](https://user-images.githubusercontent.com/61215550/181862534-510374fb-be1d-4469-8e3d-34a18ab3f90b.png)|![image](https://user-images.githubusercontent.com/61215550/181862530-1056ec06-e1e2-45d9-ac7d-c2b566b20cae.png)|

### 구성요소
#### 1. VPC ✔
- VPC: 독립된 하나의 네트워크를 구성하기 위한 가장 큰 단위
- VPC는 독립적이기 때문에 서로 통신 불가 ㅠ,ㅠ 

#### 2. Subnet ✔ 
- VPC의 IP 주소를 나누어 리소스가 배치되는 물리적 주소 범위 뜻함!
- ![image](https://user-images.githubusercontent.com/61215550/181862600-38094c67-b35d-46a3-88da-c9bb86ae0c06.png)

#### 3. Router ✔
- VPC 안에서 발생한 네트워크 요청을 처리하기 위해 어디로 트래픽을 전송해야 하는지 알려주는 **표지판 역할**
- ![image](https://user-images.githubusercontent.com/61215550/181862643-028f2512-c59b-419e-9766-6d15866c1a35.png)

#### 4. Internet Gateway ✔
- VPC 리소스와 인터넷 간 통신을 활성화 하기 위한 게이트웨이
- public subnet만 외부와 통신해야 되기에 >> public subnet 라우팅 테이블에만 인터넷 게이트웨이 향하는 규칙!!
- ![image](https://user-images.githubusercontent.com/61215550/181862710-21368621-44a9-40f4-aa9d-5fce3c637179.png)

#### 5. NAT Gateway ✔
- private subnet 인터넷연결 해주게 해준다!!
- ![image](https://user-images.githubusercontent.com/61215550/181862748-0cd2913c-b447-4e83-938d-dd079118f54b.png)

#### 6. VPC Endpoint ✔
- private link 통해 AWS 서비스와 연결함으로써 데이터를 인터넷에 노출하지 않고 바로 접근 가능!
- ![image](https://user-images.githubusercontent.com/61215550/181862792-6849f451-06f6-423c-8b22-fdb0d6623fa9.png)


### (추가) VPN
- 공중 네트워크를 통해 한 회사나 몇몇 단체가 바깥 사람에게 드러내지 않고 통신할 목적으로 쓰이는 사설 통신망
- ![image](https://user-images.githubusercontent.com/61215550/181862822-9041938b-81ad-4df6-b3b8-3fe940ee6889.png)

