# 검증과 제한 · Validation

공개 source 사본에서2026-10-27에 직접 실행한 검사입니다. 앱 source는 **1.2.0/build 253**이며 새 제품 release를 선언하지 않습니다.

## 로컬 직접 실행 · Local checks

아래 결과는 Xcode 27.1 / Swift 6.4의 로컬 공개 사본에서 얻었습니다. CI 수정 작업으로 전체 검사나 build를 다시 실행하지 않았습니다.

| 검사 | 결과 | 범위 |
| --- | --- | --- |
| Core filter | **736 PASS**, failure 0, skip 0, exit 0 | `CirclrCoreTests`. Audio/App target의 선택 검사 수는0이며 audio 전체를 실행한 것이 아님 |
| MCP contract | **39 PASS**, skip 0, exit 0 | mock RPC 기반 공개 계약 |
| MCP server | **34 PASS**, skip 0, exit 0 | 입력/schema·stdio·권한 계약 |
| cancel QA helper | **4 PASS**, skip 0, exit 0 | 선별 helper의 임시 fixture 검사 |
| demo package contract | **7 PASS**, skip 0, exit 0 | demo inventory·checksum·경로 경계 |
| release package build | **PASS**, exit 0 | main 앱과 helper 7개, 버전1.2.0/build 253 |
| strict deep signature | **PASS**, exit 0 | 생성한 로컬 앱의 ad-hoc 서명 |

Core 736은 한 번 실행한 결과이며 서로 다른 집중 검사를 합산한 수가 아닙니다. MCP와 별도 helper 검사도 각 명령의 결과를 분리해 표시했습니다. 명령은 [빌드 안내](build.md)에 있습니다.

공개 사본 구성 중 script 실행권한이 누락되어 첫 Core 명령이 exit 126으로 종료됐습니다. 원래 Git의 실행권한을 복구한 뒤 위 736검사가 통과했습니다. 앱 동작 source를 수정한 결과가 아닙니다.

`Package.swift`, `Sources`와 `Tests`의 542파일은 기준 source와 byte 동일합니다. build가 재생성한 아이콘 catalog는 별도 생성물이며 실행권한·문서·공개 구성과 구별해 대조했습니다. demo는 manifest 관리 payload 26개와 manifest 자체를 그대로 보존했습니다.

빌드 성공과 별개로 Swift 6.4 compiler에서 기존 concurrency·capture·deprecated syntax 경고가 발생했습니다. 이 공개 구성 작업에서는 기능 source를 수정하지 않았으며 warning-free build로 기록하지 않습니다.

## CI 기록 · CI status

최초 native CI는 `macos-15` ARM runner의 기본 **Xcode 16.4 / Swift 6.1.2**에서 Core 컴파일에 실패했습니다. Core step은 exit 1이며 뒤의 MCP·server·package build step은 skipped였습니다. 이를 로컬 PASS와 합산하거나 CI 통과로 표시하지 않습니다.

문서의 Xcode 26+ 조건보다 낮은 환경이 선택돼 runner 구성을 `macos-26`과 명시적인 **Xcode 26.6** developer directory로 수정했습니다. **수정된 CI 결과는 아직 이 문서에서 PASS로 확인하지 않았습니다.** 기능 source·Tests는 그대로 유지했습니다.

The first CI failed Core compilation with Xcode 16.4 / Swift 6.1.2; later steps were skipped. CI now targets macOS 26 ARM / Xcode 26.6. Its corrected run has not been recorded as passing here. Local Xcode 27.1 / Swift 6.4 results remain separate.

## 화면과 실제 실행의 범위 · Runtime boundary

동봉 screenshot 2개는 기존 build253의 원본 native capture입니다. 이번 검사에서는 앱을 시작하거나 설치하지 않았고 microphone·스피커 청취·장치/plug-in host 검증을 수행하지 않았습니다. 이전 build253 기록의 MIDI 구절 전송·커서 재생·루프 교체·섹션 재사용·저장/재열기·WAV export 결과를 이번 새 runtime 결과로 합산하지 않습니다.

물리 청취·광범위 한글 IME·기존 영상 70ms interval 문제는 남아 있습니다. 계정 대화는 기본 UI에서 비활성화돼 있으며 로컬 명령 콘솔/MCP는 유지합니다. 모든 장치·host 호환성, Apple notarization과 신규 GitHub release를 주장하지 않습니다.

Application source remains **1.2.0/build 253**. The fresh checks cover Core 736, MCP 39, server 34, cancel-helper 4, demo-contract 7, a local package build and ad-hoc signature verification. The initial missing executable mode caused exit 126 and was corrected before the passing Core run. No application launch, install, physical audio/listening, broad IME or plug-in-host validation was performed. The known 70ms video-interval issue remains open, and account chat stays disabled by default.
