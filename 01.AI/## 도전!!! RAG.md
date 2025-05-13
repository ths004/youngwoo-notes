## 도전!!! RAG 

### RAG 프로세스
####  전처리 작업
데이터를 로드해서 분할해 벡터DB에 분할한 데이터를 embedding 하여 저장한다.

#####  LOAD : 
- 문서를 로딩한다.
- 대상 ;  json,pdf ,web,등등
- Document loader :  150 개정도있다.
* 취급하는 데이터는 주로 Excel / CSV , PDF 형식
* 보안에 유리한 PDF 형식 문서가 많음
1. Document Loader 고려사항
* 한글 인코딩
* 특수 문자
2. 메터데이터 (metadata)의 종류는 어떤것이 있는가?
* page_content : 문서내용
* 페이지 번호(page)
* 표,차트,문서의 coordinates(좌표),속성 (title,table,image,text)
3.문서를 읽는 속도는 얼마나 빠른가?
* 다량의 페이지를 포함하는 문서를 업로드시 문서를 읽는 "속도"가 중요
* 실시간으로 할때 와 저장되어 있는 경우를 분리해서 중요도가 틀려짐
4. PDF Loader 종류 - fitz
* 단순하게 모든 Text를 읽어서 하나의 문자열을 합칠 때 유용 : 전체 페이지 요약
* 페이지를 읽는 속도가 가장 빠름
* 페이지 번호 제공
* 페이지 번호를 제외하고 metadata 미지원
5. PDF Loader 종류 - pyPDFLoader
* 예제 코드에 가장 많이 출현하는 방식
* 평균적으로 우수(한글 인코딩 처리,속도,metadata)
* page 단위로 데이터를 로드 : 20page PDF파일 로드시 20개의 문서로 로드
* metadata : source :파일명 , page : 페이지 번호 표기
6. PDF Loader 종류 - unstructuredPDFLoader
* 가장 많은 metadata 정보 제공
* 요소별 Load 가능 
	mode = "elements"
	페이지 안의 세부 요소에 대한 정보(좌표)가 필요하다면 좋은 Loader
* 단 속도가 다른  loader 대비 느림
    metadata 정보 중 페이지 번호를 제외한 다른 metadata 정보가 필요없다면 과감히 Skip!!
7. PDF Loader 종류 - PDFPlumber
* 한글 인코딩 처리 능력이 우수하고 다양한 metadata 정보를 제공
* 다양한  metadata 정보를 포함하고 있음(Author,ModDate)
* 단, 읽기 속도가 가장느림 (unstructuredPDFLoader 와 비슷한 수준)
  따라서 다량의 페이지를 포함하는 문서는 parsing에 꽤 많은 시간이 소요
##### SPLIT 
- 문서를 특정 기준으로 분할(Chunk) 할때 사용
- chunking 이라고 부른다.
- Text splitter  :  분할전략 10 정도
1. CharacterTextSplitter
	* 분할 사능한 최소의 단위로 분할을 시도 - 공백이나 "."을 기준으로 분할
2. RecursiveCharacterTextSplitter (상단히 좋음)
	* 일반적으로 많이 사용하는 분할 방식
	* 청크가 충분히 작아질 때까지 순서대로 분할하려고 시도
	* 기본 목록은 ["\n\n","\n"," ","" ]
	단락 --> 문장 --> 단어 순서로 함께 유지하려고 시도하는 효과가 있는데 이것 때문에 일
3. TokenTextSplitter
   * 토큰단위로 분할
   * TokenTextSplitter 를 바로 사용하면 한글 처리가 모호함
   * 따라서, KonlpyTextSplitter 를 사용하면 해결책이 될 수 있음
     -- Kkma 은 빠른 텍스트 처리보다 분석적 심도가 우선시되는 애플리케이션에 적합
4. 오픈소스
    * HuggingFace 에 업로드 된 다양한 토크나이저를 쉽게 활용 가능
    * 속도와 성능 면에서 개선된 버전이 지속적으로 업데이트 되고 있으므로, 최적의 토크나이저를 다양하게 테스트 해 볼 수 있
음
    * 신조어, 특정 도메인 용어(의료 용어) 등의 tokenizer.trainer 로 Fine-Tuning 혹은 단순 추가(add) 가능
    * 대표적인 Tokenizer
   https://github.com/huggingface/tokenizers
5. 
##### EMBED 
- 텍스트를의 벡터 표헌을 만드는 작업
기초 자료(Document Embedding)와 질문(Query Embedding) 두가지를 벡터 표현으로 만든다.  (같은 로직을 사용해야함)
한글을 고려해야함
- OpenAI Embedding(제일많이 사용) 사용시 주의 할점은 버젼이 변경시 버전이 틀릴경우 검색에  주의
   ** 비용이 필요 (캐시-CacheBackedEmbeddings를 반드시 사용해야 함 - 기초데이터)
- embedding 60 + huggingface
  https://huggingface.co/spaces/mteb/leaderboard
#####  STORE 
- 저장을 하는 시스템
- Vector Store
- Vector DB - 80개

#####  Retrivers 
- Vector DB 검색기 50개정도
- 후반부 : 서비스 단계에서 이루어지는 작업
- 질문을 embed 처리 하고 저장된 문서에서 검색 하고 LLM에 보내서 응답을 얻는다.
키워드 검색 과 

테디 RAG 우리가 절대 쉽계결과물을 얻을수 없는 이유

https://www.youtube.com/watch?v=NfQrRQmDrcc&t=1012s

### 1.Parsing, Text Chunking, Indexing


### 2. Build Embeddings

### 3. Prompt Models

### 4. RAG with Text Query

### 5. RAG with Semantic Query

### 6. RAG with Multi-Step, Hybrid Query



대규모 언어 모델을 위한 검색-증강 생성(RAG) 기술 현황 
https://discuss.pytorch.kr/t/rag-1-2/3135

https://discuss.pytorch.kr/t/rag-2-2/3160


https://dev.to/llmware/become-a-rag-professional-in-2024-go-from-beginner-to-expert-41mg