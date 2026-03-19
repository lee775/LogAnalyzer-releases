# LogAnalyzer

.NET 게임 서버 로그 분석 도구. 로컬 파일 파싱, SSH 원격 실시간 모니터링, AI 에러 분석을 지원합니다.

![.NET 8](https://img.shields.io/badge/.NET-8.0-512BD4?logo=dotnet)
![Windows](https://img.shields.io/badge/platform-Windows-0078D6?logo=windows)
![License](https://img.shields.io/badge/license-Private-gray)

## 주요 기능

### 📄 로그 파싱 & 필터링
- Serilog 포맷 자동 파싱 (타임스탬프, 레벨, 스레드ID, 핸들러 추출)
- 로그 레벨 / 핸들러 / 내용 / 시스템 필터
- 에러/경고 내용 보기
- 드래그 & 드롭, 클립보드 붙여넣기 지원

### 🌐 SSH 원격 모니터링
- PEM 키 인증으로 원격 서버 연결
- `tail -f` 기반 실시간 로그 스트리밍
- 연결 정보 자동 저장

### 🤖 AI 에러 분석
- Gemini CLI 연동 (Google 계정 인증, API Key 불필요)
- 에러 로그 선택 후 원인/상세/해결 방법 자동 분석
- 주변 컨텍스트 자동 수집

### 📊 에러 타임라인
- 시간대별 에러/경고/일반 로그 빈도 막대 차트
- 마우스 호버로 상세 위치 확인

### 🔖 북마크
- F2: 북마크 토글
- F3: 다음 북마크로 점프
- 그리드에 ★ 표시

### 🎨 하이라이트 규칙
- 키워드별 글자색/배경색 커스텀 지정
- 여러 규칙 동시 적용

### 🔔 키워드 알림
- SSH 실시간 모니터링 중 특정 키워드 감지 시 팝업 알림
- 기본값: Exception, Fatal, Critical

### 🔍 로그 비교
- 두 개 탭 로그 diff 비교
- 좌측만(빨강) / 우측만(초록) 색상 표시
- 동기화 스크롤

### 👁 실시간 파일 감시
- 파일 열기 시 자동으로 FileSystemWatcher 감시 시작
- 새로 추가된 라인 자동 표시
- `Ctrl+Shift+W`로 감시 토글 on/off
- 탭 제목에 👁 표시

### 📁 최근 파일
- 최근 열었던 파일 10개 빠른 접근

### 🗂 탭
- 여러 로그 파일/SSH 세션을 탭으로 분리
- 각 탭 독립 데이터, 북마크, SSH 연결
- Ctrl+T: 새 탭 / Ctrl+W: 닫기
- **탭 X버튼 클릭으로 닫기**
- **마우스 휠 클릭으로 탭 닫기**
- **마우스 호버 시 파일 절대경로 툴팁**
- **우클릭으로 경로 복사**

### 🖥 로컬 서버 실행
- 앱 내에서 직접 서버 프로세스 실행/종료
- Ctrl+R: 실행 / 실시간 로그 캡처
- 지정 PC에서 서버 경로 자동 설정
- ASPNETCORE_ENVIRONMENT=Development 자동 적용

### 🌙 다크 모드
- 전체 UI 다크 테마 (탭, 그리드, 메뉴, 다이얼로그 포함)
- ANSI 색상이 잘 보이는 어두운 배경
- 에러 행: 어두운 빨강 / 경고 행: 어두운 노랑

### 🎨 ANSI 색상 지원
- 서버 콘솔 출력의 ANSI 이스케이프 코드 파싱
- 16색 매핑으로 원래 색상 그대로 표시

### 🔒 파일 공유 읽기
- 서버가 쓰는 중인 로그 파일도 안전하게 열기
- FileShare.ReadWrite | Delete 모드

## 단축키

| 키 | 기능 |
|---|------|
| `Ctrl+O` | 로그 파일 열기 |
| `Ctrl+T` | 새 탭 |
| `Ctrl+W` | 탭 닫기 |
| `Ctrl+V` | 클립보드에서 붙여넣기 |
| `Ctrl+R` | 로컬 서버 실행 |
| `Ctrl+Shift+T` | 타임라인 토글 |
| `Ctrl+Shift+A` | AI 에러 분석 |
| `Ctrl+Shift+W` | 실시간 감시 토글 |
| `F2` | 북마크 토글 |
| `F3` | 다음 북마크 |

## 설치 & 실행

[Releases](https://github.com/lee775/LogAnalyzer-releases/releases)에서 `LogAnalyzer.exe` 다운로드 후 바로 실행.

- .NET 설치 불필요 (self-contained)
- Windows x64 전용

## 빌드

```bash
cd LogAnalyzer
dotnet publish -c Release -r win-x64 --self-contained true /p:PublishSingleFile=true -o publish
```

## 기술 스택

- .NET 8, Windows Forms
- [SSH.NET](https://github.com/sshnet/SSH.NET) — SSH 연결
- [Gemini CLI](https://github.com/google-gemini/gemini-cli) — AI 분석 (선택)
