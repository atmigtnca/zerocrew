hwpx-mcp-server를 글로벌로 설정해줘. 아래 단계를 순서대로 실행:

## 1단계: uvx 확인
- `which uvx`로 uvx 설치 여부 확인
- 없으면: `pip install uv` 로 설치 후 재확인
- uvx 경로를 기록 (예: /home/ubuntu/.local/bin/uvx)

## 2단계: hwpx-mcp-server 동작 확인
- `uvx hwpx-mcp-server --help` 로 패키지 사용 가능 여부 확인
- 실패하면 사용자에게 알림

## 3단계: 프로젝트 .mcp.json 설정
- 프로젝트 루트의 `.mcp.json` 파일을 확인
- 없거나 hwpx 설정이 없으면 아래 내용으로 생성/업데이트:
```json
{
  "mcpServers": {
    "hwpx": {
      "command": "[uvx 경로]",
      "args": ["hwpx-mcp-server", "--transport", "stdio"]
    }
  }
}
```
- 이미 있으면 "이미 설정되어 있습니다" 안내

## 4단계: 확인
- 설정 결과를 사용자에게 보고
- "Claude Code를 재시작하면 hwpx MCP 서버 승인 팝업이 뜹니다. '허용'을 눌러주세요." 안내

$ARGUMENTS
