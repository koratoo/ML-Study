**`Pclass`**는 **객실 등급 (Passenger Class)**을 의미하는 변수입니다. 주로 **타이타닉 데이터셋(Titanic Dataset)**에서 사용되며, 승객이 탄 선실의 등급을 나타냅니다.

### **Pclass의 의미**
- **1등급 (1st class)**: 상류층, 요금이 가장 비싸며, 생존율이 가장 높음
- **2등급 (2nd class)**: 중산층, 상대적으로 적절한 가격과 적절한 생존율
- **3등급 (3rd class)**: 노동계층, 가장 저렴한 티켓, 생존율이 가장 낮음

### **예제 데이터**
| PassengerId | Pclass | Name             | Age | Fare  |
|-------------|--------|-----------------|-----|-------|
| 1           | 1      | Allen, Miss. E  | 29  | 211.34 |
| 2           | 3      | Smith, Mr. J    | 35  | 7.25   |
| 3           | 2      | Brown, Mrs. L   | 40  | 25.00  |

여기서 `Pclass=1`이면 1등급, `Pclass=2`면 2등급, `Pclass=3`이면 3등급을 의미합니다.

### **Pclass와 생존율**
- `Pclass`는 **타이타닉 생존율**과 강한 상관관계를 갖는 변수 중 하나입니다.
- 일반적으로 1등급 승객의 생존율이 가장 높고, 3등급 승객의 생존율이 가장 낮습니다.

### **실제 분석 예시 (Python)**
```python
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

# 데이터 불러오기
titanic = sns.load_dataset('titanic')

# Pclass별 생존율 시각화
sns.barplot(x='pclass', y='survived', data=titanic)
plt.xlabel("Passenger Class")
plt.ylabel("Survival Rate")
plt.title("Survival Rate by Passenger Class")
plt.show()
```

### **결론**
- `Pclass`는 승객의 사회적, 경제적 상태를 반영하는 중요한 변수입니다.
- 모델을 만들 때 유용한 Feature로 사용될 수 있습니다.
