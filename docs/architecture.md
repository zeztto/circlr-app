# 구조 · Architecture

[문서](README.md) · [빌드](build.md)

`Package.swift`는 macOS 14 이상을 대상으로 앱·제작 CLI·audio/helper 실행 파일을 구성합니다. 외부 Swift package 의존성은 없습니다.

- `CirclrCore`: 프로젝트 모델, 곡·섹션 구조, 편집 명령, compiler, 저장과 입력 계약.
- `CirclrRealtime`: C atomic과 ring buffer를 사용하는 realtime 경계.
- `CirclrAudio`: MIDI/audio 렌더링, 파일 입출력, playback/capture와 Audio Unit 처리.
- `CirclrCodex`: 계정·로컬 도구 통합 코드. 계정 chat은 기본 앱에서 비활성화됩니다.
- `CirclrApp`: SwiftUI·AppKit 화면과 같은 문서 모델을 사용하는 편집 상태·명령 처리.
- `Tools/`: app과 별도 process로 실행하는 audio/device/trusted-MCP helper 및 제작 CLI.

`mcp/server.py`는 native 앱의 프로젝트·revision·capability를 확인하는 MCP 입구입니다. Python과 앱이 같은 편집 계약을 사용하며, snapshot/context/inspect 등 조회 전용 도구도 제공합니다.

프로젝트는 `.circlr` package로 저장합니다. 파일 보존·staging·hash 검사는 source에 있지만 이것만으로 모든 외부 파일과 장치의 호환성을 승인할 수는 없습니다. [직접 실행한 범위](validation.md)

The Swift package separates the document/editing model, realtime primitives, audio processing, account/tool integration and native interface. Helper processes and MCP use explicit document and revision boundaries. This source snapshot preserves those implementations; it does not add feature behavior.
