---
layout: single
title: "SQL 함수"
---

#### 📌 DUAL 테이블 짚고 넘어가기  

SQL 내장 함수를 실습하거나 결과값을 확인할 때 자주 사용하는 것이 바로 **DUAL 테이블**이다. 
DUAL은 오라클에서 기본 제공하는 특수 테이블로, 실제 데이터를 저장하기 위한 목적이 아니라 **연습용·함수 테스트용·시스템 정보 확인용**으로 활용된다. 


## 1) 숫자 함수 (Number Functions)
<table>
  <thead>
    <tr>
      <th style="text-align:center">함수</th>
      <th style="text-align:center">설명</th>
      <th style="text-align:left">예시 (코드)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:center"><mark><b>CEIL(n)</b></mark></td>
      <td style="text-align:center">n 이상(≥)인 값 중 가장 작은 정수 반환</td>
      <td style="text-align:left"><code>SELECT CEIL(10.123), CEIL(10.541),
        CEIL(11.001) FROM DUAL; -- 11, 11, 12</code></td>
    </tr>
    <tr><td colspan="3" style="text-align:center">					</td></tr>
    <tr>
      <td style="text-align:center"><mark><b>FLOOR
        (n)</b></mark></td>
      <td style="text-align:center">n 이하(≤)인 값 중 가장 큰 정수 반환</td>
      <td style="text-align:left"><code>SELECT FLOOR(10.123), FLOOR(10.541), FLOOR(11.001) FROM DUAL; -- 10, 10, 11</code></td>
    </tr>
    <tr><td colspan="3" style="text-align:center"></td></tr>
    <tr>
      <td style="text-align:center"><mark><b>ABS(n)</b></mark></td>
      <td style="text-align:center">부호와 관계없이 수의 크기(절대값) 반환</td>
      <td style="text-align:left"><code>SELECT ABS(10), ABS(-10), ABS(-10.123) FROM DUAL; -- 10, 10, 10.123</code></td>
    </tr>
    <tr><td colspan="3" style="text-align:center"></td></tr>
    <tr>
      <td style="text-align:center"><mark><b>ROUND
        (n, i)</b></mark></td>
      <td style="text-align:center">소수점 기준 (i+1)번째 자리에서 반올림 (i 생략 시 소수 첫째 자리 반올림)</td>
      <td style="text-align:left"><code>SELECT ROUND(10.854), ROUND(10.157,2), ROUND(115.155,-1) FROM DUAL; -- 11, 10.16, 120</code></td>
    </tr>
    <tr><td colspan="3" style="text-align:center"></td></tr>
    <tr>
      <td style="text-align:center"><b>POWER
        (base, exp)</b></td>
      <td style="text-align:center">base를 exp만큼 거듭제곱한 값 반환</td>
      <td style="text-align:left"><code>SELECT POWER(3,2), POWER(3,3), POWER(3,3.0001), POWER(-3,2) FROM DUAL; <br>-- 9, 27, 27.0029..., 9</code></td>
    </tr>
    <tr><td colspan="3" style="text-align:center"></td></tr>
    <tr>
      <td style="text-align:center"><mark><b>TRUNC
        (n, i)</b></mark></td>
      <td style="text-align:center">소수점 i자리에서 절사</td>
      <td style="text-align:left"><code>SELECT TRUNC(115.155), TRUNC(115.155,1), TRUNC(115.155,2), TRUNC(115.155,-2) FROM DUAL; -- 115, 115.1, 115.15, 100</code></td>
    </tr>
    <tr><td colspan="3" style="text-align:center"></td></tr>
    <tr>
      <td style="text-align:center">SQRT(n)</td>
      <td style="text-align:center">제곱근 반환</td>
      <td style="text-align:left"><code>SELECT SQRT(2), SQRT(5) FROM DUAL; -- 1.4142135, 2.2360679</code></td>
    </tr>
    <tr><td colspan="3" style="text-align:center"></td></tr>
    <tr>
      <td style="text-align:center"><mark><b>MOD
        <br>(n1, n2)</b></mark></td>
      <td style="text-align:center">n1을 n2로 나눈 나머지</td>
      <td style="text-align:left"><code>SELECT MOD(19,4), MOD(19.123,4.2) FROM DUAL; -- 3, 2.323</code></td>
    </tr>
    <tr><td colspan="3" style="text-align:center"></td></tr>
    <tr>
      <td style="text-align:center">EXP(n)</td>
      <td style="text-align:center">지수 함수 (eⁿ)</td>
      <td style="text-align:left"><code>SELECT EXP(2) FROM DUAL; -- 7.3890561</code></td>
    </tr>
    <tr><td colspan="3" style="text-align:center"></td></tr>
    <tr>
      <td style="text-align:center"><mark><b>REMAINDER<br>(n1, n2)</b></mark></td>
      <td style="text-align:center">MOD와 유사하나 반올림 
        <br>기준</td>
      <td style="text-align:left"><code>SELECT REMAINDER(19,4), REMAINDER(19.123,4.2) FROM DUAL;<br> -- -1, -1.877</code></td>
    </tr>
    <tr><td colspan="3" style="text-align:center"></td></tr>
    <tr>
      <td style="text-align:center">LN(n)</td>
      <td style="text-align:center">자연로그 (밑 e)</td>
      <td style="text-align:left"><code>SELECT LN(2.713) FROM DUAL;</code></td>
    </tr>
    <tr><td colspan="3" style="text-align:center"></td></tr>
    <tr>
      <td style="text-align:center">LOG
        <br>(base, n)</td>
      <td style="text-align:center">base를 밑으로 하는 로그</td>
      <td style="text-align:left"><code>SELECT LOG(10,1000) FROM DUAL; -- 3</code></td>
    </tr>
  </tbody>
</table>




### 📌 중요 수식 비교
$$
\text{MOD}(n_1, n_2) = n_1 - n_2 \cdot \text{FLOOR}\left(\frac{n_1}{n_2}\right)
$$

$$
\text{REMAINDER}(n_1, n_2) = n_1 - n_2 \cdot \text{ROUND}\left(\frac{n_1}{n_2}\right)
$$



## 2) 문자 함수

### INITCAP / LOWER / UPPER
- `INITCAP(char)` : 첫 글자만 대문자, 나머지는 소문자 (여기서, "첫 글자"는 문자열 맨 앞만 의미하는 것이 아니라, 공백·숫자·특수문자 등 알파벳이 아닌 문자를 기준으로 단어가 구분될 때마다 그 다음 알파벳을 첫 글자로 인식하여 대문자로 변환한다.)
  ```sql
    SELECT INITCAP('never say goodbye'), INITCAP('never6say*good가bye') FROM DUAL;
     -- Never Say Goodbye , Never6say*Good가bye
  ```
- `LOWER(char)` : 모두 소문자 변환
   
  ```sql
  SELECT LOWER('NEVER SAY GOODBYE') FROM DUAL; -- never say goodbye
  ```
- `UPPER(char)` : 모두 대문자 변환  
  ```sql
  SELECT UPPER('never say goodbye') FROM DUAL; -- NEVER SAY GOODBYE
  ```



### CONCAT
- `CONCAT(char1, char2)` : 문자열 연결 (연결 연산자 `||` 동일)
  
  ```sql
  SELECT CONCAT('I Have',' A Dream') FROM DUAL; -- I Have A Dream
  ```



### SUBSTR / SUBSTRB
- `SUBSTR(char, pos, len)` : 위치 기준 잘라내기
  
  ```sql
  SELECT SUBSTR('ABCDEFG',1,4) FROM DUAL; -- ABCD
  SELECT SUBSTR('ABCDEFG',-3,2) FROM DUAL; -- EF
  ```
- `SUBSTRB(char, pos, len)` : 바이트 단위 잘라내기
   
  ```sql
  SELECT SUBSTRB('가나다라마바사',1,4) FROM DUAL; -- 가(한글은 3byte 단위)
  ```

### LTRIM / RTRIM
- `LTRIM(char, set)` : 왼쪽에서 지정 문자 제거  
- `RTRIM(char, set)` : 오른쪽에서 지정 문자 제거
   
  ```sql
  SELECT LTRIM('ABCDEFGABC','ABC'), LTRIM('가나다라','가'),
       RTRIM('ABCDEFGABC','ABC'), RTRIM('가나다라','라') FROM DUAL; -- DEFGABC , 나다라 , ABCDEFG , 가나다
	
   SELECT LTRIM('가나다라','나'), RTRIM('가나다라','나') FROM DUAL; -- 다라 , 가나다라

  ```



### LPAD / RPAD
- `LPAD(expr1, n, expr2)` : 왼쪽 채우기  
- `RPAD(expr1, n, expr2)` : 오른쪽 채우기  
 ```sql
  CREATE TABLE EX4_1(PHONE_NUM VARCHAR2(30));
  INSERT INTO EX4_1 VALUES('111-1111');
  INSERT INTO EX4_1 VALUES('111-2222');
  INSERT INTO EX4_1 VALUES('111-3333');
  SELECT LPAD(PHONE_NUM,9,'(02)') FROM EX4_1; -- (111-1111 , (111-2222 , (111-3333
  SELECT RPAD(PHONE_NUM,12,'(02)') FROM EX4_1; -- 111-1111(02) , 111-2222(02) , 111-3333(02)
 ```


### REPLACE / TRANSLATE

- `REPLACE(char, search_str, replace_str)` : 문자열 단위로 치환 
- `TRANSLATE(expr, from_str, to_str)` : 문자 단위로 1:1 치환 


 ```sql
SELECT REPLACE('나는 너를 모르는데 너는 나를 알겠는가?','나','오리') FROM DUAL;
-- 오리는 너를 모르는데 너는 오리를 알겠는가?
  SELECT LTRIM(' ABC DEF'), RTRIM(' ABC DEF D '), REPLACE(' A BC DEF',' ','') FROM DUAL;
-- 'ABC DEF' , ' ABC DEF D' , 'ABCDEF'
 ```
>
> ```sql
SELECT
    EMPLOYEE_ID, EMP_NAME, TRANSLATE(EMP_NAME,'ABCDEFGHIJKLMNOPQRSTUVWXYZ','ITSBEENALONGDAYWITHOUTMYFREIN') AS TRANS_NAME
FROM employees; -- 
```
![](https://velog.velcdn.com/images/meongkune/post/eb690140-bdac-46c8-a450-b3346a5b612f/image.png)

## INSTR / LENGTH / LENGTHB

* `INSTR(str, substr, pos, occur)` : 
  **str**에서 **substr**과 일치하는 문자열의 위치를 반환하며,**pos**는 검색을 시작할 위치,
  **occur**는 몇 번째로 일치하는 문자열을 찾을 것인지를 지정한다. (단, 해당 문자열이 존재하지 않으면 0을 반환한다.)
* `LENGTH(char)` : 문자열 길이 **문자 기준** 으로 반환
* `LENGTHB(char)` : 문자열 길이 **Byte 기준** 으로 반환

 ```sql
  SELECT
      INSTR( '내가 만약 외로울 때면,내가 만약 괴로울 때면,내가 만약 즐거울 때면', '만약') AS INSTR1,
      INSTR( '내가 만약 외로울 때면,내가 만약 괴로울 때면,내가 만약 즐거울 때면', '만약', 5) AS INSTR2,
      INSTR('내가 만약 외로울 때면,내가 만약 괴로울 때면,내가 만약 즐거울 때면','만약',5, 2) AS INSTR3
  FROM DUAL; -- 4, 17, 30
 ```
 ```sql
  SELECT LENGTH('대한민국'),LENGTHB('대한민국') FROM DUAL; -- 4, 8
 ```

출처 : https://huimang2.github.io/algorithm/gcd_lcm

