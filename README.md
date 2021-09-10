# 수행결과

## 문제점
<br>

### 1. 'SpringBoot' 가동시
#### 오류: WriteDTO 경로 오류
> 원인: WriteDAO.xml 내 resultType 경로 오류

### --- WriteDAO.xml ---
```java
/*오류*/
<select id="selectByUid" resultType="com.lec.spring.WriteDTO">
/*수정*/
<select id="selectByUid" resultType="com.lec.spring.domain.WriteDTO">
```
<br><br>

### 2. '수정' 시 /board/updateOk.do 
#### 오류 : String > int 변환불가
>원인: parameter 값이 아니라 uid 라는 이름의 문자열로 전달

### --- UpdateOk.jsp ---
```java
/*오류*/location.href = "view.do?uid=${uid}"; 
/*수정*/location.href = "view.do?uid=${param.uid }";
```
<br><br>


### 3. '삭제' 시 /board/deleteOk.do 
#### 오류: SQL에서 uid 값을 찾지못함
>원인: DELETE 쿼리문 오류

### --- WriteDAO.xml ---
```java
/*오류*/ DELETE FROM test_write WHERE uid=#{uid}
/*수정*/ DELETE FROM test_write WHERE wr_uid=#{uid}
```
<br><br>

### 4. '글 작성' 시 /board/write.do
#### 오류: 글 작성 시 작성자란 제목란 비었을 경우 팝업창 연속 두번 발생
>원인: return flase 미기입

### --- Write.jsp ---
```java
/*오류*/
if(name == ""){
		alert("작성자 란은 반드시 입력해야 합니다");
		frm['name'].focus();
	}
/*수정*/
if(name == ""){
		alert("작성자 란은 반드시 입력해야 합니다");
		frm['name'].focus();
		return false;
	}

```



