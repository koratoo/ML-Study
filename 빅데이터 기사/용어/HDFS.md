### HDFS(Hadoop Distributed File System)란?
HDFS(Hadoop Distributed File System)는 **Hadoop의 분산 스토리지 시스템**으로, 대규모 데이터 처리를 위해 설계된 파일 시스템이다. 여러 대의 서버에 데이터를 분산 저장하고 관리하며, 대용량 데이터를 효율적으로 저장하고 처리할 수 있도록 한다.

---

## 🔹 **HDFS의 주요 특징**
### 1. **분산 저장(Distributed Storage)**
   - 데이터를 여러 개의 노드(Node)에 분산하여 저장한다.
   - 대용량 데이터를 처리하는 데 적합하며, 장애 발생 시에도 데이터 손실을 최소화할 수 있다.

### 2. **마스터-슬레이브 아키텍처(Master-Slave Architecture)**
   - **NameNode(네임노드)**: 파일 시스템의 메타데이터(파일명, 위치, 블록 정보 등)를 관리하는 **중앙 서버** 역할.
   - **DataNode(데이터노드)**: 실제 데이터를 저장하는 **서버 노드**들로, NameNode의 지시에 따라 동작한다.

### 3. **블록 단위 저장(Block-based Storage)**
   - 데이터를 고정 크기의 블록(기본 128MB) 단위로 나누어 저장.
   - 여러 개의 DataNode에 분산 저장하여 데이터 손실을 방지.

### 4. **데이터 복제(Replication)**
   - 기본적으로 데이터를 **3개 복제**(Replication Factor = 3)하여 저장.
   - 장애 발생 시 다른 노드에서 데이터를 복구 가능.

### 5. **고장 감내(Fault Tolerance)**
   - 특정 노드가 다운되더라도 다른 노드에 복제된 데이터를 사용하여 복구 가능.
   - NameNode가 데이터 상태를 모니터링하고 복구 절차를 자동으로 수행.

### 6. **높은 처리량(High Throughput)**
   - 대량의 데이터를 빠르게 읽고 쓰는 데 최적화.
   - 대규모 데이터 분석과 머신러닝 등에 유용.

---

## 🔹 **HDFS의 구성 요소**
| 구성 요소  | 역할 |
|-----------|---------------------------------|
| **NameNode**  | 메타데이터(파일 위치, 블록 매핑) 관리 |
| **DataNode**  | 실제 데이터 블록 저장 및 관리 |
| **Secondary NameNode** | NameNode의 메타데이터 백업 역할 |
| **Client** | HDFS와 상호작용(파일 업로드, 다운로드) |

---

## 🔹 **HDFS의 동작 방식**
1️⃣ **파일 저장 (Write Operation)**
   - 클라이언트가 HDFS에 파일 업로드 요청.
   - NameNode가 파일을 블록으로 나누고, DataNode에 저장할 위치 지정.
   - 각 블록이 여러 개의 DataNode에 복제되어 저장됨.

2️⃣ **파일 읽기 (Read Operation)**
   - 클라이언트가 파일을 요청하면 NameNode가 해당 파일의 블록 위치를 알려줌.
   - 클라이언트가 해당 DataNode에서 블록을 읽어와 조합.

3️⃣ **데이터 복제 및 복구**
   - 특정 DataNode가 다운되면 NameNode가 이를 감지하고 다른 DataNode에서 복제본을 만들어 균형 유지.

---

## 🔹 **HDFS의 장점**
✅ **대규모 데이터 저장 가능**: 페타바이트(PB) 단위의 데이터 저장 가능  
✅ **확장성(Scalability)**: 노드를 추가하여 용량 확장 가능  
✅ **데이터 안정성**: 데이터 복제(Replication)로 장애 대응  
✅ **고속 데이터 처리**: MapReduce와 함께 사용하여 대용량 데이터 분석 최적화  

---

## 🔹 **HDFS의 단점**
❌ **실시간 처리 어려움**: 배치 처리(Batch Processing)에 적합하며, 실시간 분석에는 부적합  
❌ **소규모 파일 비효율적**: 작은 파일이 많으면 NameNode의 메타데이터 부담 증가  
❌ **랜덤 쓰기 불가**: 한 번 저장된 파일을 수정하는 기능이 부족 (Append 방식만 지원)  

---

## 🔹 **HDFS vs 일반 파일 시스템 비교**
| 비교 항목  | HDFS | 일반 파일 시스템 |
|----------|----------------|----------------|
| **데이터 저장 방식** | 분산 저장 | 단일 서버에 저장 |
| **파일 크기** | 대용량(GB~PB) | 일반적으로 수 MB~GB |
| **데이터 복제** | 자동 복제(기본 3개) | 별도 백업 필요 |
| **확장성** | 노드 추가로 용량 확장 가능 | 제한적 |
| **고장 감내** | 노드 장애 발생 시 자동 복구 | 서버 장애 시 데이터 손실 |

---

## 🔹 **HDFS 사용 사례**
✅ **빅데이터 분석** (Hadoop 기반 데이터 처리)  
✅ **머신러닝/AI 데이터 저장소** (Spark, TensorFlow와 연계)  
✅ **로그 및 이벤트 저장소** (웹 로그, IoT 데이터 수집)  
✅ **대용량 데이터 아카이브** (이미지, 비디오, 센서 데이터 저장)

---

## 🔹 **HDFS를 사용할 수 있는 도구**
📌 **Hadoop CLI** → `hdfs dfs -put file.txt /user/hadoop/`  
📌 **Apache Spark** → HDFS에서 데이터 읽고 처리 가능  
📌 **Hive, HBase** → SQL 쿼리 및 실시간 데이터 저장  

---

### 📌 **결론**
HDFS는 **대규모 데이터 저장과 분석을 위한 분산 파일 시스템**으로, **확장성**, **데이터 안정성**, **고속 처리** 등의 강점을 가지고 있다. 그러나 실시간 처리에는 적합하지 않으며, 작은 파일 관리가 비효율적이라는 단점도 있다. Hadoop 생태계의 핵심 기술로, 빅데이터 분석, 머신러닝, 로그 저장 등의 분야에서 널리 활용된다.
