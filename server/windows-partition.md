## 윈도우 파티션
> [참고자료](https://coding-factory.tistory.com/492)
- 파티션 나눈다 = 하나의 하드 디스크를 마치 두개의 하드디스크처럼 사용하는 것
- 😛 듀얼 운영체제 사용할때 / 하드디스크 따로 나누어 관리하고 싶을 경우
  - [듀얼 운영체제 하는 방법](https://mesnotes.tistory.com/1)
### 윈도우 디스크 용량 확인(참고)
> [참고자료](https://zetawiki.com/wiki/%EC%9C%88%EB%8F%84%EC%9A%B0_%EB%94%94%EC%8A%A4%ED%81%AC_%EC%9A%A9%EB%9F%89_%ED%99%95%EC%9D%B8)
- ![image](https://user-images.githubusercontent.com/61215550/204440436-a3684814-e6ea-4fa8-8e52-5b1b75de5be8.png)
#### 방법1. diskmgmt.msc
- ![image](https://user-images.githubusercontent.com/61215550/204440493-989a7797-e27c-4f88-9a90-d9a79677eb95.png)
#### 방법2. wmic
```shell
C:\Users\zetawiki>wmic diskdrive get deviceid,model,size
DeviceID            Model                               Size
\\.\PHYSICALDRIVE0  Hitachi HDS721010CLA332 ATA Device  1000202273280
\\.\PHYSICALDRIVE1  SAMSUNG SSD 830 Series ATA Device   128034708480


C:\Users\zetawiki>wmic logicaldisk get name,size
Name  Size
C:    31457275904
D:    96574894080
E:    1000202240000

```
#### 방법3. diskpart
```shell
C:\Users\zetawiki>echo list disk | diskpart | findstr GB
  디스크 0    온라인        931 GB           0 B   *
  디스크 1    온라인        119 GB       1024 KB


C:\Users\zetawiki>echo list volume | diskpart | findstr GB
  볼륨 0     E   DATA        NTFS  기본          931 GB  정상            시스템
  볼륨 1     C   System      NTFS  파티션          29 GB  정상            부팅
  볼륨 2     D   Virtual     NTFS  파티션          89 GB  정상

```
#### 방법4. Get-WmiObject `PowerShell`
```shell
C:\Users\zetawiki>PowerShell "Get-WmiObject Win32_DiskDrive | FT DeviceID,@{E={\"{0:N1} GiB\" -F($_.Size/1000000000)}} -H -A" | FindStr G | Sort
\\.\PHYSICALDRIVE0 1,000.2 GiB
\\.\PHYSICALDRIVE1 128.0 GiB

C:\Users\zetawiki>PowerShell "Get-WmiObject Win32_DiskDrive | FT DeviceID,@{E={\"{0:N1} GB\" -F($_.Size/1GB)}} -H -A" | FindStr G | Sort
\\.\PHYSICALDRIVE0 931.5 GB
\\.\PHYSICALDRIVE1 119.2 GB

C:\Users\zetawiki>PowerShell "Get-WmiObject Win32_LogicalDisk -F DriveType=3 | FT DeviceID,@{E={\"{0:N1} GB\" -F($_.Size/1GB)}} -H -A" | FindStr G
C:       29.3 GB
D:       89.9 GB
E:       931.5 GB

```

