## `mybatis` 부등호, 비교연산자 사용 방법
> [참고자료](https://codingmomong.tistory.com/404)

### 1. 해결방법. `CDATA`
```
<!-- <![CDATA[  ]]> 사용 -->
<select id="getEmployeeSalary">
    SELECT 
    	EMPLOYEE_ID
    FROM
    	EMPLOYEE
    WHERE
    	SALARY <![CDATA[<]]> 10000
</select>
```
### 2. `gt` `lt`
```
<!-- gt, lt 사용 -->
<select id="getEmployeeSalary">
    SELECT 
    	EMPLOYEE_ID
    FROM
    	EMPLOYEE
    WHERE
    	SALARY &lt; 10000
</select>
```
### 3. when, if 절 test에 부등호 사용 방법
```
<!-- gt, lt 사용 -->
<select id="getEmployeeSalary">
    SELECT 
    	EMPLOYEE_ID
    FROM
    	EMPLOYEE
    WHERE
    	1=1
        <if test="salary lt 10000>
    	AND DEPT = '1000'
        </if>
</select>
```
