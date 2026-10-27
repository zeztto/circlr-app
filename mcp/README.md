# 로컬 MCP · Local MCP

[소개](../README.ko.md) · [구조](../docs/architecture.md)

실행 중인 circlr의 프로젝트를 조회하고 편집하는 Python MCP server입니다. 기본 연결은 앱이 제공하는 trusted helper를 사용합니다. `--socket`은 명시한 legacy socket에 연결하는 경로입니다.

```sh
python3 mcp/server.py --help
python3 mcp/server.py --read-only
```

`--read-only`는 snapshot/context/inspect/ports/sounds/job/events 조회만 허용합니다. 편집·저장·export·record는 해당 사용자 작업의 권한과 fresh project/revision이 필요합니다. microphone 도구를 단순 연결 확인용으로 실행하지 마세요.

`Resources/Codex`의 agent kit는 Python 3.11+ installer와 역할 지침을 포함합니다. 설치기는 사용자의 선택한 Codex 설정에 쓰므로 먼저 도움말과 변경 대상을 확인하세요.

```sh
python3 Resources/Codex/install.py --help
```

계약 검사는 실제 앱을 필요로 하지 않습니다.

```sh
PYTHONDONTWRITEBYTECODE=1 python3 -m unittest discover -s Tests -p 'test_mcp_*.py'
PYTHONDONTWRITEBYTECODE=1 python3 mcp/test_server.py
```

The server supports read-only inspection and explicit revision-bound changes. Account chat is a separate disabled feature. No native smoke script or private song fixture is included in this source snapshot.
