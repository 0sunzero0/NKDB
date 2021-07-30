# Capstone Project : KUBIC(Korea Unification Bigdata Center)
https://kubic.handong.edu
## 통일 빅데이터 센터란
### 소개
현재, 북한과 통일에 관련된 정보를 필요로 하는 사람은 증가하고 있으나 기존 서비스에서는 북한과 통일에 관한 전문적인 정보를 얻기 어렵습니다. 
북한 및 통일 연구 분야는 주제가 갖는 국지성 및 언어적 특성으로 인해, 데이터 자원이 생성, 공유되는 커뮤니티의 크기는 매우 한정적입니다.
따라서 대다수 상용 검색 엔진들은 검색 결과의 중요도를 계산하는 과정에서 관련 데이터 자원을 중요하지 않다고 판단하는 경우가 많고, 결과적으로 해당 자료들은 검색 노출 후순위로 나타나게 됩니다.
<br>
이를 위해, 본 프로젝트는 기존 검색엔진의 문제점을 해결하고 <북한, 통일 관련 전문 학술 자료>를 제공하는 "빅데이터 검색엔진"을 제작하였습니다.
### 진행 기간
2019.06.24-2020.06.05

## 구현 결과
![Total](https://user-images.githubusercontent.com/29566893/127668397-e4757251-193c-47cc-b707-0466eba520d0.png)
- 통일 빅데이터 센터 데이터 검색엔진 개발
- 북한과 통일 관련 자료 13,400건 자료 수집 및 검색 가능
- 한국과학기술연구원과의 MOU
- 논문 : 정보과학회논문지, 20.06.21, 북한 및 통일 문헌 빅데이터 검색 엔진 설계 및 사례 연구

## 배운점
- 1년 단위 프로젝트 수행하면서 배운 것이 많았지만 그 중에서는 가장 크게 배운 것은 적극적인 태도와 협력하는 마음과 끝까지 하고자 하는 태도입니다.
  - 처음 교수님, 팀원과 미팅을 가졌을 때는 부족한 실력을 보여주고 싶지 않다는 생각이 많이 들었지만, 피하고 싶다는 생각보다 어떻게 하면 해결할 수 있을지에 대해 집중하려고 노력했습니다.
  - 프로젝트 전에는 문제를 추상적으로 느끼면 시도하는 것을 힘들어 하고 미루는 문제가 있었는데 프로젝트 하면서 극복할 수 있게 되었습니다. 문제를 피하기보다는 문제에 다가가고 못하는 부분을 솔직하게 말하는 연습을 하면서 문제해결능력을 기르게 되었습니다.
  - 프로젝트를 할 때 복잡한 문제를 만났을 시, 생각을 정리하고 어떤 것이 문제점인지 파악하고 문제 해결할 때까지 검색하여 해결한 경험이 쌓이게 되었습니다. 그로 인해 문제가 발생해도 해결할 때까지 검색하고 연구해보고 의논하면 해결할 수 있다는 자신감을 가지게 되었습니다.
- 프로젝트 수행하면서 배웠던 함께 하는 마음과 적극적인 사고를 가지고 앞으로 타 프로젝트할 때 팀원이 할 수 있도록 응원해주고 환경을 만들어주고 될 때까지 해결하는 태도를 가져 상대방에게 좋은 영향을 주는 사람이 될 것입니다.

## 소프트웨어 스택 설계
![SystemDesign](https://user-images.githubusercontent.com/29566893/127630569-c0f54cec-f503-4a46-adda-632ead9bb979.png)

## 프로젝트 핵심 내용
1) 북한 및 통일 연구 문헌에 대한 전문적인 검색 서비스를 제공할 수 있는 소프트에어 스택 설계 및 구현
2) 북한, 통일 연구 문서가 수집되는 데이터 사일로(data silo) 형성
- 지정된 북한, 통일 연구기관의 웹사이트로부터 각종 문서 데이터를 자동으로 탐색, 수집할 수 있도록 크롤러의 작동부 구현 (Scrapy 사용)
- PDF, HWP, DOCX, DOC 등 다양한 형식의 파일로부터 문서의 내용이 수합될 수 있도록 크롤러 기능 확장 (Tika, java-hwp 사용)
3) 검색 서비스를 위한 역-인덱스 데이터베이스 구축
- 수집한 문서 데이터에 대한 원할한 검색을 위하여, 역-인덱스 생성 및 검색엔진 DB 구성 (Elasticsearch 사용) 연구자료저장(인덱싱)
4) 검색 시 사용작 원하는 문석 검색 순위 상위에 노출될 수 있도록 랭킹 알고리즘 적용
- BM25 알고리즘을 적용하여 검색 결고 노출 순위 결정
![BM25](https://user-images.githubusercontent.com/29566893/127631112-03e43a65-cb43-4217-b682-4f723009b172.png)
- 향후 다양한 랭킹 알고리즘을 추가하여 검섹 엔지 최적화를 지속할 수 있도록 확장가능한 구조 구현
5) 검색 수행 테스트르 위한 front-end 구현 (데모)
- 사용자가 검색어를 입력했을 떄에 입력 데이터를 쿼리로 변경하여 검색엔진에 전달하고 얻은 데이터를 다시 송출
- 별도의 front-end 개발팀이 보다 체계적이고 다양한 시각화가 가미된 사용자 인터페이스를 설계 중

## 실험 결과 및 평가
### 수행결과
1) 사전 지정된 76개 북한 및 통일 연구기관 웹사이트로부터 총 13820건의 문서 데이터 수집 및 저장 완료
2) 수집된 문서에 대하여 한국어 형태소 분석 및 역-인덱싱 완료
3) 역인덱싱 된 문서에 관하여 문서 제목, 문서 내용, 작성 기관, 첨부파일 제목, 첨부파일 내용 등에 대한 검색 가능
4) 검색 시 검색어와 매칭 점수가 높은 순으로 검색 결과 제공
5) 수집된 문서에 대하여 약 54만개 단어 분량의 북한 및 통일 연구 말뭉치 생성
### 기대효과
1) 유관분야 연구자들에게 효과적인 자료 검색 기능을 제공
- 세부 분야 전문가들이 스스로 ROI를 지정하고, 손쉽게 품질 좋은 전문 검색엔진을 구축할 수 있도록 하는 소프트웨어 솔루션의 완성 
2) 사전 지식이 없는 사용자도 쉽게 사용할 수 있는 검색 도구 제공
- 연관 분야에 대한 접근성 증대 및 통일에 대한 긍정적 인식 확산
### 앞으로의 연구 방향
- 지속적으로 신규 문서들을 수집 및 역인덱싱
- 다양한 랭킹 알고리즘을 적용/튜닝하여 데이터에 적합한 랭커 완성 
- 한국어와 외국어가 동시에 처리될 수 있도록 프레임워크 확장
- 사용자의 의도에 더욱 부합하는 결과물을 제공하기 위한 쿼리 확장 (단어사전 추가, 쿼리로그 활용)

## 업무 분담
### back-end
- 0sunzero0 (PM, 개발자):
  - 기획 : 과제 문제화 및 구체화 
  - 크롤링 : 13820건 문서 추출, 첨부파일 내용 추출 및 저장(text, image, table etc), 첨부파일 DB에 저장, 크롤링 자동화
  - 인덱싱 : 데이터 관리 오픈소스 공부 (🔎 Elasticsearch)
  - 랭킹 알고리즘 : Scoring 조사, 랭킹 생성 알고리즘 연구, 데이터 텍스트 분석, 단어 말뭉치 생성
  - 쿼리 프로세싱 : 매칭 구조 구현, 쿼리 결과 디자인
  - 프로토타입 제작 : 서버 구축, 프론트엔드와의 연결, 검색 수행 테스트를 위한 front-end 구현
- Kim, Miso (개발자) :
  -  기획 : 과제 문제화 및 구체화
  -  인덱싱 : 데이터 관리 오픈소스 공부, 데이터 싱크 맞추기, 형태소 분석기 적용하여 인덱스 생성, 인덱스 생성 자동화
  -  랭킹 알고리즘 : 데이터 텍스트 분석
### front-end
통일교육선도대학사업의 일환으로 진행 중인 본 검색 엔진 개발 연구에서는 현재 80여개 유관 기관의 웹사이트를 지속적으로 모니터 및 신규 게시되는 문서 자원을 확보해가고 있습니다.
산출된 백엔드를 기반으로 "텍스트 데이터의 다양한 시각화"를 담당하는 [프론트엔드](https://github.com/HGUISEL/TIBigdataFE) 설계와 함께 사용성이 뛰어난 북한 및 통일 문헌 검색 엔진 공개를 목표를 두고 있습니다.

## 사용 기술
### 핵심 
- Crawling
- Indexing
- Ranking Algorithm
- Query Processing

### 개발언어 / 툴 
: Python, Java, Web 개발 언어 （HTML, CSS, JAVASCRIPT）, NOSQL, MongoDB, Elasticsearch, Jython, Java-hwp 
