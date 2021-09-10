# 수행결과

## 문제점
### 1. '수정' 시 /board/updateOk.do 
#### 오류 : String > int 변환불가
>원인: parameter 값이 아니라 uid 라는 이름의 문자열로 전달

```java
/*오류*/location.href = "view.do?uid=${uid}"; 
/*수정*/location.href = "view.do?uid=${param.uid }";
```


### 1. '삭제' 시 /board/deleteOk.do 
#### 오류: SQL에서 uid 값을 찾지못함
>원인: DELETE 쿼리문 오류
```java
/*오류*/ DELETE FROM test_write WHERE uid=#{uid}
/*수정*/ DELETE FROM test_write WHERE wr_uid=#{uid}
```

