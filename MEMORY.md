# gksdud Memory

## 현재 상태
```yaml
status: done
last_agent: antigravity
last_branch: main
last_session: 2026-10-04T19:28+09:00
session_count: 1
```

## 프로젝트 개요
macOS에서 딜레이와 글자 씹힘 없이 빠릿빠릿한 한/영 전환을 제공하는 오픈소스 메뉴바 유틸리티 앱.

## 기술 스택
- Swift 5, AppKit, Carbon, IOKit
- macOS HID Keyboard Modifier Mapping API (`HIDKeyboardModifierMappingSrc` / `Dst`)
- Homebrew Cask 배포

## 아키텍처 결정
- Karabiner 대체: 무거운 키 리매핑 도구 대신 단독 경량 앱(`gksdud`)으로 한/영 전환 처리.
- F19 가상 키 매핑: 우측 Command 등 선택한 키를 F19에 매핑하고 즉시 Down/Up 이벤트를 트리거하여 글자 씹힘 해결.

## 코드 컨벤션
- 표준 에이전트 ID: claude-code / claude-desktop / claude-web / claude-mobile / gemini-cli / antigravity / opencode / other.

## 알려진 제약사항
- 자체 서명 빌드로 인해 `com.apple.quarantine` 해제 및 macOS [손쉬운 사용] 접근성 권한 허용 필수.
- Karabiner-Elements 삭제 시 DriverKit 시스템 확장(`org.pqrs.Karabiner-DriverKit-VirtualHIDDevice`)은 SIP 정책상 macOS 시스템 설정 UI에서 수동 비활성화 필요.

## 하지 말 것
- Karabiner 제거 시 앱 아이콘(`/Applications`)만 삭제하고 방치하지 말 것 (백그라운드 가상 HID 드라이버 프로세스가 계속 상주함).

## 세션 로그
| session_end | agent | branch | status | summary |
|---|---|---|---|---|
| 2026-10-04T19:28+09:00 | antigravity | main | done | gksdud 리포 파악, Homebrew 설치(/Applications/gksdud.app), quarantine 해제 및 기존 Karabiner 잔여 파일/드라이버 완전 정리 |
