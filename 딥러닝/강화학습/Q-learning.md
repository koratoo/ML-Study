Q러닝(Q-learning)은 **강화학습(Reinforcement Learning, RL)**에서 사용하는 대표적인 알고리즘 중 하나야. 딥러닝에서 강화학습을 적용할 때도 Q러닝이 활용될 수 있어.

### 🔹 Q러닝이란?
Q러닝은 **가치를 기반(Value-based)**으로 행동을 선택하는 **모델 프리(Model-free) 강화학습** 알고리즘이야. 즉, 환경(Environment)과 보상(Reward)에 대한 명확한 모델 없이도 학습할 수 있는 방법이지.

### 🔹 핵심 개념
- **Q-값(Q-value)**: 특정 상태(s)에서 특정 행동(a)을 했을 때 기대할 수 있는 **미래 보상의 총합**을 의미해.
- **Q-테이블(Q-table)**: 모든 상태(s)와 행동(a)에 대한 Q-값을 저장하는 테이블.
- **벨만 방정식(Bellman Equation)**: Q값을 업데이트하는 핵심 공식.

![image](https://github.com/user-attachments/assets/82130d8f-ac5a-4875-8a86-60a1bd052af0)


  - \( Q(s, a) \) : 현재 상태 \( s \)에서 행동 \( a \)를 했을 때의 Q-값
  - \(![image](https://github.com/user-attachments/assets/34f42c1d-bd47-46d1-a996-f35e72812510)
) : 현재 행동에 대한 보상
  - \(![image](https://github.com/user-attachments/assets/a1ff7b91-4f2a-4482-8c5c-d10c3c9a5f1e)
) : 할인율 (future reward의 중요도 조절)
  - \(![image](https://github.com/user-attachments/assets/72bcfcb7-247e-412f-bfdf-949c804b66ea)
) : 다음 상태 \( s' \)에서 가능한 최대 Q-값
  - \( ![image](https://github.com/user-attachments/assets/fea4a5e0-bef3-4947-a809-56966839f3e7)
) : 학습률

### 🔹 Q러닝의 과정
1. **초기화**: Q-테이블을 0 또는 랜덤 값으로 설정
2. **반복 수행**:
   - 현재 상태(s)에서 행동(a) 선택 (ε-greedy 사용 가능)
   - 선택한 행동을 실행하고, 보상(r)과 다음 상태(s')를 얻음
   - Q-테이블 업데이트
   - 상태(s')를 새로운 상태(s)로 변경
3. **학습 종료**: 충분한 학습 후 최적의 정책을 도출

### 🔹 Q러닝 vs. 딥 Q 네트워크(DQN)
- Q러닝은 **Q-테이블을 직접 저장**하지만, 상태 공간이 커지면 저장이 어려움.
- DQN(Deep Q-Network)은 **뉴럴 네트워크를 활용해 Q-값을 근사**하여 더 복잡한 문제도 해결할 수 있음.

### 🔹 어디에 쓰일까?
- 게임 AI (예: 알파고, 강화학습 기반 AI)
- 로봇 제어
- 자율 주행
- 주식/금융 트레이딩 등

Q러닝은 강화학습의 기초적인 알고리즘이면서도 매우 강력한 방법이야! 🚀
