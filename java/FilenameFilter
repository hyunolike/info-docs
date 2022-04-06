## `FilenameFilter`
> [참고 자료](https://wiper2019.tistory.com/250)
- 특별한 파일명이나 혹은 확장자명을 가진 파일 리스트만 추출해야 하는 경우
- FilenameFilter >> interface(~할수 있는) 강제적으로 구현 !! ✔
- `interface FileFilter` `FilenameFilter` >> 특정 파일, 디렉토리를 필터링하여 리스트 추출할 필요가 있을 때 사용

### File class 파일 내부 리스트 찾는 메소드 종류
- `public String[] list(FilenameFilter filter);` : 디렉토리의 파일목록을 String 배열로 반환
- `public File[] listFiles(FileFilter filter);` : FileFilter 인스턴스에 구현된 조건에 맞는 File을 배열로 반환
- `public File[] listFiles(FilenameFilter filter);` : FilenameFilter 인터페이스가 구현된 조건에 맞는 File 배열로 반환 ✔ 이걸로 실습

### 실습
```java
// sam 확장자명 파일 갯수 구하는 로직
File dir = new File("D:\\sam");
File[] files = dir.listFiles(new FilenameFilter() {
    @Override
    public boolean accept(File dir, String name) {
        return name.toLowerCase().endsWith(".sam");
    }
});
System.out.printf(String.valueOf(files.length));

// 결과
// 5
```

