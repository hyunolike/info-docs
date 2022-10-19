## 브라우저 데이터 저장 방식
> [참고자료](https://ko.javascript.info/data-storage)
- 크게 3가지
  - 쿠키와 document.cookie
  - localStroage & sessionStorage
  - IndexedDB
- ![image](https://user-images.githubusercontent.com/61215550/196570878-c84d4aa0-6e3e-4a12-97f3-90771ef56142.png)

### IndexedDB
> [참고자료](https://www.youtube.com/watch?v=mHJDtDM_wHc)
- [코드자료](https://gist.github.com/egoing/22b86994518b69e7ed938371ca7f8972)


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
