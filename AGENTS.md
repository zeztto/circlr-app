# circlr 공개 소스 유지관리

- 한국어를 기본으로 하고 기술명·identifier는 English로 유지한다.
- 이 사본의 앱 코드는 1.2.0/build 253 source snapshot이다. 문서·공개 구성 변경을 새 제품 릴리스나 전체 제품 검증으로 보고하지 않는다.
- 코드·테스트·resource 변경은 범위를 정하고 관련 검사와 diff를 검토한다. 실제 장치·마이크·앱 실행은 해당 작업의 명시적 권한과 격리 환경에서만 수행한다.
- 빌드 명령은 현재 checkout의 Resources 생성물과 dist 앱을 만든다. 다른 checkout·설치 앱·기존 프로젝트를 교체하지 않는다.
- 개인 곡·샘플·자격 증명·운영 로그·로컬 설정·private 대화 식별자는 commit하지 않는다.
- root MIT와 제3자 고지를 유지한다. Demos는 별도 조건이며 CC0·Public Domain 원본과 새 작곡·편곡의 권리를 섞지 않는다.
- `.github`의 CI와 문서에 선언한 검사를 보존한다. 실패·미실행·물리 청취·IME·device 호환 범위를 구별해 보고한다.
- 저장 구조·MCP·audio의 실제 변경에는 영향에 맞는 회귀 검사를 수행한다. docs-only 변경에 native build를 무조건 반복하지 않는다.

```sh
./scripts/swift-local.sh test --scratch-path .build/publication-tests --filter CirclrCoreTests
PYTHONDONTWRITEBYTECODE=1 python3 -m unittest discover -s Tests -p 'test_mcp_*.py'
```

빌드·범위는 [빌드 안내](docs/build.md)와 [검증 기록](docs/validation.md)을 따른다.
