# WAL 파일이란? (Write Ahead Log)

* 직역하면 "로그 선행 기입" 이다.
* 데이터베이스 시스템에서 ACID 의 특성 가운데 `원자성`과 `내구성`을 제공하는 기술의 한 계열이다.
* __WAL 을 사용하는 시스템의 모든 수정은 적용 이전에 "로그"에 기록된다. 일반적으로 redo 및 undo 정보는 둘 다 로그에 저장된다.__
* 한 예로 어느 프로그램이 특정 작업을 수행하는 동안 컴퓨터에 정전이 일어났다고 하자.
* 다시 시작할 때 프로그램은 어느 작업이 수행을 성공적으로 마쳤는지, 절반 성공했는지, 아니면 실패했는지를 잘 알고 있어야 한다.
* 로그 선행 기입이 사용된다면 프로그램은 이러한 로그를 검사하여 예기치 않은 정전 시 해야할 일과 실제로 했던 일을 비교하게 된다.

## WAL 을 사용하는 데이터베이스

* PostgreSQL 데이터베이스 시스템은 WAL을 사용하여 포인트 인 타임 복구와 데이터베이스 복제 기능을 제공한다.[1]
* SQLite 데이터베이스도 WAL을 지원한다.[2]
* 몽고DB는 로그 선행 기입을 사용하여 일관성과 충돌 안전을 제공한다.
* 아파치 HBase는 WAL을 사용하여 재난 후 복구를 제공한다.
* grafana Tempo
