## 임시 데이터 저장소 만들기
- 필요 클래스
  - 엔티티
  - 임시 데이터베이스 엔티티
- 필요 기술
  - `ConcurrentHashMap`

### 1. 엔티티 생성
```java
public class Order{
    private String id = null;
    private int quantity = 0;
    private String date = null;
    private String status = null;
    private boolean complete = false;

    public Order(){}

    public Order(String id, int quantity, String date, String status, boolean complete) {
        this.id = id;
        this.quantity = quantity;
        this.date = date;
        this.status = status;
        this.complete = complete;
    }

    public String getId() {
        return id;
    }

    public void setId(String id) {
        this.id = id;
    }

    public int getQuantity() {
        return quantity;
    }

    public void setQuantity(int quantity) {
        this.quantity = quantity;
    }

    public String getDate() {
        return date;
    }

    public void setDate(String date) {
        this.date = date;
    }

    public String getStatus() {
        return status;
    }

    public void setStatus(String status) {
        this.status = status;
    }

    public boolean isComplete() {
        return complete;
    }

    public void setComplete(boolean complete) {
        this.complete = complete;
    }
}
```

### 2. 임시 데이터 저장소 생성
```java
/**
 * RDBMS 대체하기 위한 임시 메모리 데이터 저장소
 */
public class OrderDB {
    private static OrderDB orderDB = null;
    private Map<String, Order> persistence = new ConcurrentHashMap<String, Order>(); ⭐

    static public OrderDB getInstance(){
        if(orderDB == null){
            orderDB = new OrderDB();
        }
        return orderDB;
    }

    public Order findById(String id){
        return persistence.get(id);
    }

    public int save(Order order){
        SimpleDateFormat format = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
        Date time = new Date();
        order.setDate(format.format(time));

        persistence.put(order.getId(), order);

        return 1;
    }

    public int delete(String id){
        persistence.remove(id);

        return 1;
    }

    public List<Order> findAll(){ 
        List<Order> list = new ArrayList<>(persistence.values());
        return list;
    }
}
```
