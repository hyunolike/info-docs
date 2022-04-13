## `File` 클래스
> [참고 자료](https://devbox.tistory.com/entry/Java-File-%ED%81%B4%EB%9E%98%EC%8A%A4)

- 파일, 디렉토리 다루는 기능
- File 인스턴스는 __파일__ 일수도 있고 __디렉토리__ 일수도 있다.

### 1. `File` 클래스 생성자
|클래스 생성자|설명|
|-------------|-----|
|`File(File parent, String Child)`|parent 객체 폴더의 child라는 파일에 대한 File객체 생성|
|`File(String pathname)`|`pathname`에 해당하는  파일의 File 객체 생성|
|`File(String parent, String child)`|parent 폴더 경로의 child라는 파일에 대한 File객체 생성|
|`File(URI uri)`|file url 경로에 대한 파일의 File 객체 생성|

### 2. `list()` `listFiles()` 메소드 이용해 디렉터리의 파일 목록 출력
- `String[] list()`: 디렉토리의 파일목록(디렉토리 포함)을 __String__ 배열로 반환
- `String[] list(FilenameFilter filter)`: `FilenameFilter` 인스턴스에 구현된 조건에 맞는 배열을 __String__ 배열로 반환 
- `File[] listFiles()`: 디렉토리의 파일목록(디렉토리 포함)을 __File__ 배열로 반환

```java
import java.io.File;
 
public class DirList{
   
    public static void main(String[] args) {
    //C:\디렉토리 아래 있는 파일 또는 디렉토리 목록을 얻어 도스 콘솔에 출력하세요.
    //File클래스의 list(), listFiles()메소드 이용.
       
        String dirName = "C:\\";
        File dir = new File(dirName);
        String files[] = dir.list();
        //디렉토리의 파일목록(디렉토리포함)을 String배열로 반환
       
        System.out.println(dir.list()); //배열의 주소값 출력.
       
        /*for(String fn : files) //확상for문 ; for -each문
            System.out.println(fn);
        */
           
        /*for(int i=0; i<files.length;i++){
            System.out.println(files[i]);
        }*/
       
        System.out.println("--------------------------------------");
        System.out.println("파일/DIR명\t size");
        System.out.println("--------------------------------------");
        File[] files2 = dir.listFiles();
        //디렉토리의 파일목록(디렉토리포함)을 File 배열로 반환
        for(File f: files2){
            String str = f.getName();
       
            if(f.isDirectory()){
                System.out.print(str+"\t");
                System.out.print("DIR\n");
            }else{ //파일인 경우 ... txt파일만 출력.
                if(str.endsWith(".txt")){              
                    System.out.print(str+"\t"+ f.length()+"bytes\n");
                }
               
            }
           
        }//for-------
       
    }
}
[출처] [JAVA] 예제 - File클래스의 list() , listFiles() 메소드를 이용해서 디렉터리의 파일목록 출력|작성자 자바킹
```
