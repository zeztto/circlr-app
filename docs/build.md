# 빌드와 테스트 · Build and tests

[소개](../README.ko.md) · [검증 기록](validation.md)

필수 환경은 macOS 14+, full Xcode 26+와 Python 3입니다. `xcode-select`로 선택한 developer directory에서 `xcrun actool`, `sips`, `iconutil`, Swift를 사용할 수 있어야 합니다. agent-kit installer는 Python 3.11+의 `tomllib`를 사용합니다.

## Core와 MCP

```sh
./scripts/swift-local.sh test --scratch-path .build/publication-tests --filter CirclrCoreTests
PYTHONDONTWRITEBYTECODE=1 python3 -m unittest discover -s Tests -p 'test_mcp_*.py'
PYTHONDONTWRITEBYTECODE=1 python3 mcp/test_server.py
```

Core fixture는 선별 보존한 `qa/r30-create-fixture.py`와 baseline JSON을 사용합니다. MCP 검사는 mock RPC 기반 계약 검사이며 실행 중인 앱이나 microphone에 연결하지 않습니다. 전체 Swift/audio test를 실행하기 전에는 test의 장치 접근 여부를 읽고 범위를 정하세요.

## 앱 패키지

```sh
./scripts/build-app.sh
codesign --verify --deep --strict 'dist/써클러.app'
```

현재 checkout의 icon·agent kit를 생성하고 `dist/써클러.app`을 만듭니다. 같은 checkout에 기존 앱이 있으면 archive에 보존한 뒤 교체합니다. 다른 설치 경로나 기존 사용자 앱을 다루지 않습니다. 빌드 명령은 앱을 자동 실행하지 않습니다.

현재 package에는 앱과 audio/device/trusted-MCP helper, agent kit, 별도 조건의 demo가 함께 들어갑니다. Demos inventory와 asset checksum이 맞아야 packaging을 완료합니다. ad-hoc 서명은 Apple notarization이 아닙니다.

The build uses the current checkout only. It regenerates icons/agent-kit metadata and stages an ad-hoc signed app without launching it. Device, listening, IME and host compatibility checks are separate.
