## RAG for Complex PDFs

* core constructs for LlamaIndex Stack up to Advanced retrieval 
* Deal with unstructured(text) and structured(table) data at the same time

🙋 RAG
🦙 LlamaIndex
📄 The PDF Problem
❓ Conclusions, QA

### RAG (RETREIVAL AUGMENTED GENERATION)
* Retrieval : Finds references in your documents
* Augmented : Adds references to your prompts
* Generation : Better answers to questions!


https://colab.research.google.com/drive/1AyKbc6DYU3b9gWq52SU7qacH7q8DeKOf?usp=sharing

https://colab.research.google.com/drive/1ffaV5iFRvhzGIq8YSckf-VJ-y0AZFmA-?usp=sharing

https://www.canva.com/design/DAF2T6jNxuk/5HNaXFnIas1oE5bKCCLHkg/view

### 벡터 데이터베이스란
벡터 데이터베이스는 수학적 표현으로 저장된 데이터의 모음입니다. 벡터 데이터베이스를 사용하면 머신 러닝 모델이 이전 입력을 더 쉽게 기억할 수 있으므로 강력한 검색, 추천, 텍스트 생성 사용 사례에 머신 러닝을 사용할 수 있습니다. 정확한 일치 대신 유사성 메트릭을 기반으로 데이터를 식별할 수 있으므로 컴퓨터 모델이 맥락에 맞게 데이터를 이해할 수 있다.

벡터 데이터베이스는 몇 년 전 신경망에 기반한 차세대 검색 엔진을 구동하기 위해 처음 등장했습니다. 오늘날에는 조직이 GPT4와 같은 대규모 언어 모델을 기반으로 애플리케이션을 배포할 수 있도록 지원하는 새로운 역할을 하고 있습니다.

벡터 데이터베이스는 표 형식의 데이터를 행과 열로 저장하도록 구축된 PostgreSQL과 같은 표준 관계형 데이터베이스와는 다릅니다. 또한 데이터를 JSON으로 저장하는 MongoDB와 같은 최신 NoSQL 데이터베이스와도 구별됩니다. 그 이유는 벡터 데이터베이스는 벡터 임베딩이라는 한 가지 유형의 데이터만 저장하고 검색하도록 설계되었기 때문입니다.

벡터 임베딩은 머신 러닝 프로세스의 학습 단계에서 출력으로 생성되는 학습 데이터의 증류된 표현입니다. 이는 추론 과정에서 새로운 데이터를 처리하는 필터 역할을 합니다.


-- Run Chroma DB on a local machine and as a Docker container.
https://abhishektatachar.medium.com/run-chroma-db-on-a-local-machine-and-as-a-docker-container-a9d4b91d2a97
-- RAG Tutorial: Exploring AnythingLLM and Vector Admin
https://dev.to/worldlinetech/in-bed-with-gpt-and-nodejs-4kh2

#### 참고 사항 링크 
- 벡터 데이터 베이스 랭킹
https://lakefs.io/blog/12-vector-databases-2023/

https://db-engines.com/en/ranking/vector+dbms
- chroma 
 https://www.trychroma.com/
 
 -- How to Ingest a PDF File into a Vector Database
 https://engineering-technologists.com/2024/01/15/how-to-ingest-a-pdf-file-into-a-vector-database/
 
 
 https://engineering-technologists.com/2023/12/20/vector-db-vs-graph-db-why-and-what-are-the-differences/