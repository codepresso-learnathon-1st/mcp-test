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

## TODO
- [ ] [예시 케이스](https://github.com/teddynote-lab/mcp-usecase/blob/main/case1/mcp_server.py) 참고해 동작 확인

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
