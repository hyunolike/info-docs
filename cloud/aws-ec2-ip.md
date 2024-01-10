## AWS EC2 고정IP 연결
> [참고자료](https://assaeunji.github.io/aws/2020-03-30-elastic-ip/)
### Elastic IP
- EC2 인스턴스(가상서버) > 시작 및 정지 > 공인 ip 주소 변경
- ⭐이유!! ip주소는 40억 대까지 한정!
- `AWS` IP 자원 활용 위해 > 인스턴스 중지 > IP 주소 회수!
  - 방지방법! `고정IP(Elastic IP)` 할당
- 주의할점.
  - 고정ip > 인스턴스 연결 필수! > 과금 ❌
