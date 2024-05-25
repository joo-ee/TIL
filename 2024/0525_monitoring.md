### Elastic Search와 Kibana

프로젝트 배포가 급해 하루하루 소홀했다 ... 😶

ElasticSearch는 검색엔진이자 분산저장소로, 일반적으로 JSON 형식의 데이터를 저장하며 루씬 기반으로 개발되어있어 빠른 검색이 가능하다.

> 루씬(Lucene)이란 ?
> Apache Lucene이라는 고성능, 오픈 소스 검색 엔진 라이브러리를 의미. Lucene은 텍스트 검색 및 인덱싱 기능을 제공하는 자바 라이브러리로, 매우 빠르고 효율적인 검색 기능을 제공하는 데 특화되어 있다.

Elastic Search는 서비스의 검색을 위해 사용되거나, 로그 등의 데이터를 검색할때 자주 사용된다.

> ELF 스택
> 로그 데이터를 수집(Filebeat), 처리(Logstash), 저장 및 검색(Elasticsearch)하는 데 사용
> **E**lasticsearch: 데이터 저장 및 검색 담당.
> **L**ogstash: 로그 수집 및 처리 도구. Logstash는 다양한 소스에서 데이터를 수집하고, 필터링, 변환하여 Elasticsearch에 저장한다.
> **F**ilebeat: 로그 파일 데이터를 수집하는 경량의 데이터 수집기. Filebeat는 로그 파일에서 데이터를 읽어 Logstash나 Elasticsearch로 전송한다.

> EFK 스택
> 로그 데이터를 수집(Fluentd), 저장 및 검색(Elasticsearch), 시각화(Kibana)하는 데 사용
> **E**lasticsearch: 로그 데이터 저장 및 검색 담당.
> **F**luentd: 로그 수집 및 처리 도구. Fluentd는 다양한 소스에서 데이터를 수집하고, 필터링, 변환하여 Elasticsearch에 저장한다.
> **K**ibana: 데이터 시각화 도구. Kibana는 Elasticsearch에 저장된 데이터를 시각화하여 분석할 수 있게 한다.

#### Kibana

Kibana는 ElasticSearch 데이터를 시각화하고 탐색하는 데 사용되는 도구로, 결과를 시각화하는 기능과 dsl을 질의할 툴을 제공하는 등 추가기능을 제공합니다. 데이터의 형태를 만들고, Elastic Stack을 탐색할 수 있게 하는 시각화 및 관리 서비스이다.

주요 기능은 다음과 같다.

- 데이터 시각화: Elasticsearch에 저장된 데이터를 다양한 차트, 그래프, 맵 등의 시각화 도구로 표현한다.
- 대시보드 생성: 사용자가 원하는 형태로 대시보드를 만들어 실시간 데이터를 모니터링할 수 있다.
- 검색 및 분석: Kibana는 Elasticsearch의 DSL(도메인 특정 언어)을 사용하여 복잡한 쿼리를 쉽게 작성하고 실행할 수 있는 인터페이스를 제공한다.

다양한 시각화를 통해서 데이터를 분석할 수 있는 툴인 것 같은데 팀에서는 로그 확인용으로만 사용 중이라서 조금 아쉽다 ？
