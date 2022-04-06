## zip 파일 압축, 압축 해제 `zip` `unzip`
> [참고 자료](https://intrepidgeeks.com/tutorial/zip4j-in-java-compression-and-decompression-zip)
- `zip4j` 라이브러리: 암호 걸린 zip 파일 생성

### 자바에서 압축이 필요할 때
- 사용자 요청한 데이터 압축 >> 다운로드 가능하도록 파일로 보내줄 때
- 로그를 파일에 쌓고 파일을 압축하거나 로그 파일의 내용(문자열)을 압축해서 데이터베이스에 저장할 때
- 압축파일 내부에 `.exe` 파일 있는지 검사할 때(조금 다른 예시)


### 실습
```java
ZipFile zipFile = new ZipFile("d:\\sam\\test.zip");

ArrayList fileToAdd = new ArrayList();
fileToAdd.add(new File("d:\\sam\\test.sam"));
fileToAdd.add(new File("d:\\sam\\test1.sam"));

ZipParameters parameters = new ZipParameters();
parameters.setCompressionMethod(CompressionMethod.DEFLATE);
parameters.setCompressionLevel(CompressionLevel.NORMAL);

zipFile.addFiles(fileToAdd, parameters);
```
