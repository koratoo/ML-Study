빅데이터에서 **Sqoop (SQL to Hadoop)** 은 **Hadoop과 관계형 데이터베이스(RDBMS) 간의 데이터 전송을 수행하는 도구**야.

---

### 📌 **Sqoop이란?**
- **"SQL + Hadoop"**의 합성어로, **RDBMS(MySQL, PostgreSQL, Oracle 등) ↔ Hadoop(HDFS, Hive, HBase 등)** 간 대량의 데이터를 효율적으로 이동하는 오픈소스 툴.
- Apache에서 개발한 프로젝트이며, **MapReduce 기반으로 병렬 처리**하여 성능을 최적화함.

---

### ✅ **Sqoop의 주요 기능**
1. **데이터 가져오기 (Import)**
   - RDBMS → Hadoop (HDFS, Hive, HBase 등)으로 데이터를 가져옴.
   - 예시: MySQL 데이터 → HDFS로 이동
     ```sh
     sqoop import --connect jdbc:mysql://localhost:3306/mydb --username root --password mypass --table mytable --target-dir /hdfs/path
     ```

2. **데이터 내보내기 (Export)**
   - Hadoop → RDBMS로 데이터를 보냄.
   - 예시: HDFS 데이터 → MySQL로 이동
     ```sh
     sqoop export --connect jdbc:mysql://localhost:3306/mydb --username root --password mypass --table mytable --export-dir /hdfs/path
     ```

3. **테이블 목록 가져오기**
   - RDBMS에 있는 모든 테이블을 확인
     ```sh
     sqoop list-tables --connect jdbc:mysql://localhost:3306/mydb --username root --password mypass
     ```

4. **데이터베이스 전체 가져오기**
   - 데이터베이스의 모든 테이블을 한 번에 HDFS로 가져옴.
     ```sh
     sqoop import-all-tables --connect jdbc:mysql://localhost:3306/mydb --username root --password mypass --warehouse-dir /hdfs/path
     ```

---

### 🚀 **Sqoop의 장점**
- **병렬 처리**를 사용하여 대량의 데이터를 빠르게 이동 가능
- **JDBC 드라이버 지원**으로 다양한 데이터베이스와 연동 가능
- **Hadoop 에코시스템(HDFS, Hive, HBase 등)과 통합 용이**
- **증분 로드 지원**: 새로운 데이터만 가져오는 기능 제공
  ```sh
  sqoop import --connect jdbc:mysql://localhost:3306/mydb --username root --password mypass --table mytable --incremental append --check-column id --last-value 1000
  ```

---

### 💡 **Sqoop을 사용해야 하는 경우**
- 대량의 데이터를 **관계형 데이터베이스(RDBMS)에서 Hadoop으로 이동**할 때
- Hadoop에서 처리된 데이터를 **RDBMS로 다시 저장**할 때
- **정기적인 데이터 동기화**가 필요할 때

---

### 🔥 **Sqoop과 유사한 도구**
- **Apache Nifi**: 데이터 이동 자동화 도구
- **Apache Flume**: 로그 데이터를 Hadoop으로 전송
- **Kafka Connect**: 실시간 데이터 스트리밍 기반 전송

---

### 📌 **정리**
- **Sqoop은 RDBMS ↔ Hadoop 간 데이터 이동을 위한 도구**
- **대량 데이터 이동을 병렬 처리로 최적화**
- **HDFS, Hive, HBase와 통합하여 활용 가능**
- **증분 로드 기능으로 실시간 데이터 동기화 가능**

이제 Hadoop을 사용할 때 관계형 DB와 데이터를 주고받을 일이 있으면 Sqoop을 활용하면 돼! 🚀
