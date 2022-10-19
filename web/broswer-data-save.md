## 브라우저 데이터 저장 방식
> [참고자료](https://ko.javascript.info/data-storage)
- 크게 3가지
  - 쿠키와 document.cookie
  - localStroage & sessionStorage
  - IndexedDB
- ![image](https://user-images.githubusercontent.com/61215550/196570878-c84d4aa0-6e3e-4a12-97f3-90771ef56142.png)

### 참고 자료
|서버 데이터 저장|클라이언트 데이터 저장|
|-------------------|------------|
|![image](https://user-images.githubusercontent.com/61215550/196576307-21ad9e6a-5569-44e0-9223-39cbb824a5da.png)|![image](https://user-images.githubusercontent.com/61215550/196575692-d5da3cc1-0706-4421-8335-e409f309631a.png)|


### IndexedDB
> [참고자료](https://www.youtube.com/watch?v=mHJDtDM_wHc)
- [코드자료](https://gist.github.com/egoing/22b86994518b69e7ed938371ca7f8972)



```
IndexedDB는 쿠키나 localstorage 처럼 
웹브라우저에 내장된 데이터베이스 기능입니다. 

이 기능을 이용하면 매우 큰 용량의 데이터를 
사용자의 브라우저에 저장할 수 있습니다. 

데이터를 서버로 전송하지 않아도 되기 때문에 
성능을 높이고, 
비용을 줄이고, 
보안을 강화할 수 있습니다. 

```

```html
<!DOCTYPE html>
<html>
    <body>
        <script>
            // create database
            const dbReq = indexedDB.open('opentutorials',1);
            let db;
            dbReq.addEventListener('success', function(event){
                db = event.target.result;
            });
            dbReq.addEventListener('error', function(event){
                const error = event.target.error; 
                console.log('error', error.name);
            });            
            dbReq.addEventListener('upgradeneeded', function(event){
                db = event.target.result;  
                let oldVersion = event.oldVersion;
                if(oldVersion < 1){
                    db.createObjectStore('topics', {keyPath:'id', autoIncrement:true});
                } 
            });
        </script>
        
        <input type="button" value="add" onclick="
            let store = db.transaction('topics', 'readwrite').objectStore('topics');
            let addReq = store.add({
                title:prompt('title?'),
                body:prompt('body?')
            });
            addReq.addEventListener('success', function(event){
                console.log(event);
            });
        ">
        <input type="button" value="get" onclick="
            let id = Number(prompt('?id'));
            let store = db.transaction('topics', 'readonly').objectStore('topics');            
            let getReq = store.get(id);
            getReq.addEventListener('success', function(event){
                console.log(event.target.result);
            });
        ">
        <input type="button" value="list" onclick="
            let store = db.transaction('topics', 'readonly').objectStore('topics');            
            let getAllReq = store.getAll();
            getAllReq.addEventListener('success', function(event){
                console.log(event.target.result);
            });
        ">
        <input type="button" value="update" onclick="
            let store = db.transaction('topics', 'readwrite').objectStore('topics');
            let putReq = store.put({
                id:Number(prompt('id?')),
                title:prompt('title?'),
                body:prompt('body?')
            });
            putReq.addEventListener('success',function(event){
                console.log(event);
            });
        ">
        <input type="button" value="delete" onclick="
            let store = db.transaction('topics', 'readwrite').objectStore('topics');
            let deleteReq = store.delete(Number(prompt('id?')));
            deleteReq.addEventListener('success', function(event){
                console.log(event);
            });
        ">        
    </body>
</html>
```
