# mcp-test
Claude Desktop(MCP Client) 이용해 예제 MCP Server 간 동작 테스트를 해보자

## Skills
- [Fastmcp](https://github.com/jlowin/fastmcp)
- uv 패키지
 
## 패키지 설치
- requirements.txt에 있는 패키지 설치

```shell
pip install -r requirements.txt
```

## 예시 케이스 코드 
```
case1/
└── rag/
    ├── __init__.py
    ├── base.py              ← RAG 검색 추상화 클래스
    ├── pdf.py               ← PDF 특화 RAG 구현
    ├── config.py            ← 경로 및 설정 값
    ├── auto_mcp_json.py     ← MCP 실행을 위한 config JSON 생성기
    └── mcp_server.py        ← 실제 MCP 서버 진입점

```


### 예시 케이스 진행 실행 요약
1. PDF 파일 /data/*.pdf 에 넣기
2. .env에 OPENAI_API_KEY 정의
3. python auto_mcp_json.py 실행 → mcp_config.json 생성
4. MCP 런타임에서 rag-mcp 실행
5. MCP와 연결된 클라이언트가 semantic_search("What is LangChain?") 쿼리 전송
6. 검색 결과 마크다운 형태로 응답

## TODO
- [x] [예시 케이스](https://github.com/teddynote-lab/mcp-usecase/blob/main/case1/mcp_server.py) 참고해 동작 확인

## 테스트 결과
### 1차 기본 동작 확인 :: ✅정상동작
- 데모 MCP Server를 작성해 Fastmcp로 설치하고, 클로드 앱에서 동작 확인

```shell
❯ fastmcp install mcp_server.py
# Demo MCP server
[03/28/25 23:26:48] INFO     Added server 'Demo' to Claude config                                                                              claude.py:125
                    INFO     Successfully installed Demo in Claude app   
                                        
open -a Claude
```

### 2차 예시케이스 확인 :: ✅정상동작
```shell
# [1] MCP config 생성
python case1/auto_mcp_json.py

# [2] 생성된 config.json을 클로드 데스크탑 설정에 복사

# [3] 클로드 데스크탑 실행
open -a Claude
```

#### 2차 예시케이스 클로드 데스크탑 동작 캡쳐
##### 1. 연결 확인
<img width="582" alt="image" src="https://github.com/user-attachments/assets/86a5a8d8-421e-40bf-bfee-084bf1171b12" />

##### 2. 질문
<img width="771" alt="image" src="https://github.com/user-attachments/assets/6ee518b0-4186-4c5d-b82b-748f656a33f1" />
<img width="649" alt="image" src="https://github.com/user-attachments/assets/0cc8623e-a683-436d-9a1b-72c855de6202" />

