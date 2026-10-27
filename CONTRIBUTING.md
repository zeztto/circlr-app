# 기여 안내 · Contributing

코드·문서 기여에는 [MIT License](LICENSE)를 적용합니다. 외부 코드·자산의 출처와 license를 밝히고 [기존 고지](THIRD_PARTY_NOTICES.md)를 유지하세요. 개인 음악·샘플·자격 증명은 첨부하지 마세요.

Code and documentation contributions use MIT. Declare third-party sources/licenses and retain their notices. Do not attach private music, samples or credentials.

변경은 한 문제에 집중하고 문제·바뀐 동작·실행한 검사·남은 제한을 설명합니다. 앱의 UI·audio 변경은 해당 실제 동작에 맞는 검증이 필요합니다. 문서만 바꾸면 링크·양쪽 언어·diff를 확인합니다.

Keep a change scoped. Describe the problem, behavior, checks and limits. UI/audio changes need relevant runtime evidence; documentation changes need link and language checks.

```sh
./scripts/swift-local.sh test --scratch-path .build/publication-tests --filter CirclrCoreTests
PYTHONDONTWRITEBYTECODE=1 python3 -m unittest discover -s Tests -p 'test_mcp_*.py'
```

[빌드와 테스트](docs/build.md) · [에이전트 규칙](AGENTS.md)
