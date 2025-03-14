### 📌 **데이터프레임의 인덱스(Index)와 헤더(Header)**
Pandas의 `DataFrame`은 **행(row)과 열(column)으로 구성된 2차원 데이터 구조**이며,  
각각의 **행은 "인덱스(Index)"**, **열은 "헤더(Header)"**를 가집니다.

---

## ✅ **1. 인덱스(Index)란?**
인덱스(Index)는 **각 행을 식별하는 고유한 값**이며, 기본적으로 0부터 시작하는 숫자로 자동 생성됩니다.

```python
import pandas as pd

data = {
    "이름": ["철수", "영희", "민수"],
    "나이": [25, 30, 22],
    "성별": ["남", "여", "남"]
}

df = pd.DataFrame(data)
print(df)
```
**출력 결과:**
```
    이름  나이 성별
0   철수  25  남
1   영희  30  여
2   민수  22  남
```
✅ **왼쪽의 `0, 1, 2`가 인덱스(Index)**  
✅ **기본적으로 0부터 시작하는 정수형 인덱스가 자동 부여됨**

### **🔹 인덱스를 설정하는 방법**
#### 1️⃣ 특정 컬럼을 인덱스로 지정 (`set_index()`)
```python
df = df.set_index("이름")
print(df)
```
**출력 결과:**
```
     나이 성별
이름        
철수   25  남
영희   30  여
민수   22  남
```
✅ **이제 '이름' 컬럼이 인덱스 역할을 함**

#### 2️⃣ 인덱스 초기화 (`reset_index()`)
```python
df = df.reset_index()
print(df)
```
**출력 결과:**
```
    이름  나이 성별
0   철수  25  남
1   영희  30  여
2   민수  22  남
```
✅ **인덱스를 다시 숫자로 초기화하고 기존 인덱스는 컬럼으로 복원됨**

---

## ✅ **2. 헤더(Header)란?**
헤더(Header)는 **각 열(Column)의 이름(컬럼명)**을 의미하며, `DataFrame`의 첫 번째 행에 위치합니다.

```python
print(df.columns)
```
**출력 결과:**
```
Index(['이름', '나이', '성별'], dtype='object')
```
✅ `['이름', '나이', '성별']` → **이것이 헤더(Header)**

### **🔹 헤더(컬럼명) 변경 방법**
#### 1️⃣ `columns` 속성 변경
```python
df.columns = ["Name", "Age", "Gender"]
print(df)
```
**출력 결과:**
```
   Name  Age Gender
0  철수   25    남
1  영희   30    여
2  민수   22    남
```
✅ **컬럼명이 "이름 → Name", "나이 → Age", "성별 → Gender"로 변경됨**

#### 2️⃣ 특정 컬럼명만 변경 (`rename()`)
```python
df = df.rename(columns={"이름": "Name", "나이": "Age"})
print(df)
```
✅ 특정 컬럼만 변경할 수 있음

---

## 🎯 **정리**
| 개념  | 설명 |
|------|--------------------------------|
| **인덱스 (Index)** | 행(Row)을 구분하는 식별자 (기본: 0부터 시작하는 숫자) |
| **헤더 (Header)** | 열(Column)의 이름(컬럼명) |

✔ **인덱스는 행을 식별하는 역할**  
✔ **헤더는 컬럼(열)의 이름을 나타냄**  
✔ **인덱스는 `set_index()`, 헤더는 `rename()`으로 변경 가능**  

🚀 Pandas에서 데이터를 다룰 때 인덱스와 헤더를 제대로 이해하면 더 쉽게 데이터를 조작할 수 있습니다!
