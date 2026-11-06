# EasyDoStudio

OBS 대신 쓰려고 만든 Windows 화면 녹화 · 영상 편집 프로그램입니다. 원하는 화면만 골라 녹화하고, 소스별로 볼륨을 따로 잡고, 녹화한 영상을 바로 잘라 붙이고 자막까지 넣어 내보냅니다. EasyDo 시리즈.

## 다운로드

최신 버전 0.2.1 — [Releases](https://github.com/parkrye/DesktopProject_EasyDoStudio/releases)에 exe 두 개가 있습니다. 하나만 받아 실행합니다. 설치 과정은 없습니다.

| 파일 | 크기 | 조건 |
|---|---|---|
| `EasyDoStudio-0.2.1-standalone.exe` | 약 78MB | .NET 설치 없이 바로 실행 |
| `EasyDoStudio-0.2.1.exe` | 약 28MB | [.NET 9 Desktop Runtime](https://dotnet.microsoft.com/download/dotnet/9.0) 필요 |

받은 파일은 Release 본문의 SHA-256으로 확인할 수 있습니다. 처음 실행할 때 Windows SmartScreen 경고가 뜰 수 있습니다 (`추가 정보 → 실행`). 새 버전은 앱 안 `설정 → 앱 정보 → 새 버전 받기`에서 받을 수 있습니다.

### 같이 필요한 것

- **Windows 10 2004 이상** (Windows 11 권장. 녹화 중 노란 캡처 테두리 없애기, 앱별 소리 녹음은 Windows 10 21H2 이상)
- **FFmpeg** — 녹화 · 편집 · 자막 생성에 씁니다. 명령 프롬프트에서 한 번만 설치하면 앱이 알아서 찾습니다.

  ```
  winget install Gyan.FFmpeg
  ```

  다른 곳에 둔 ffmpeg를 쓰려면 `설정 → FFmpeg`에서 경로를 지정합니다.

### 처음 켜면

1. 데스크톱 오디오와 마이크가 믹서에 자동으로 들어옵니다.
2. 소스 `+`에서 녹화할 모니터 · 창 · 영역을 고릅니다.
3. **녹화 시작**(또는 `Ctrl+Shift+F9`). 다시 누르면 저장됩니다.
4. **편집기**에서 방금 녹화한 파일을 열어 자르고, 자막을 넣고, 내보냅니다.

## 기능

| 영역 | 내용 |
|---|---|
| 녹화 소스 | 모니터 전체 · 특정 창 · 드래그로 고른 화면 영역 · 웹캠 · 이미지(PNG 투명도) · 텍스트(글꼴 · 색 · 외곽선 · 배경 상자), 화면 소스마다 마우스 커서 보이기 / 숨기기 |
| 화면 구성 | 장면 여러 개, 소스 겹치기 · 순서 · 표시/숨김, 미리보기에서 끌어 옮기기 · 모서리로 크기 조절(가장자리 · 가운데 자석 정렬), 화면 맞추기 · 채우기 · 원본 크기 |
| 오디오 | 마이크 · 스피커 출력 · **특정 앱 소리만**, 소스별 볼륨 · 음소거 · 레벨 미터, 기본 장치가 바뀌면 자동으로 다시 연결 |
| 녹화 | mkv / mp4, 해상도 · fps · 비트레이트 설정, NVENC · AMF · QSV 하드웨어 인코더 자동 감지(없으면 x264), **오디오를 소스별 트랙으로 나눠 저장**, 일시정지 |
| 편의 | 전역 단축키(게임 중에도 동작), 트레이 아이콘(녹화 상태 색상, 메뉴로 녹화 · 일시정지), 장면 · 설정 자동 저장 |
| 편집기 | 썸네일 · 파형 타임라인, 자르기 · 구간 삭제 · 순서 바꾸기 · 되돌리기, **구간별 속도(0.25~4배) · 음높이 · 역재생 · 페이드 · 볼륨**, 여러 파일 이어붙이기, 트랙별 볼륨을 다시 섞기, mp4 / mkv 내보내기 |
| 화면 효과 | 색 보정 프리셋(흑백 · 세피아 · 빈티지 · 따뜻하게 · 차갑게 · 시네마틱 · 선명한 색), 밝기 · 대비 · 채도 · 감마, 흐림 · 선명 · 모자이크 · 비네트 · 뒤집기, 켄 번스 · 펀치 인 · 흔들림, **전환 16종**(디졸브 · 페이드 · 와이프 · 슬라이드 · 원형 · 확대 · 픽셀화 · 흐림) |
| 이미지 · 음악 | 이미지 구간 · 빈 구간 넣기, **편집 중 화면 캡처를 바로 정지 화면 · 오버레이로**, 이미지 오버레이(PIP · 워터마크), 배경 음악 줄(자르기 · 배속 · 음높이 · 볼륨 · 페이드), 말할 때 음악 자동 줄이기, 음량 평준화 |
| 편집 편의 | 편집 프로젝트 저장 / 열기(.edproj), 미리보기 · 타임라인 휠 확대, 영상 여는 동안 로딩 화면, 내보낸 파일 자동 검사(해상도 · fps · 길이 · 소리 · 싱크 · 디코딩 오류) |
| 자막 | 음성 인식(Whisper)으로 자동 생성, 직접 추가 · 수정 · 시간 맞추기, 긴 문장 자동 줄바꿈 · 나누기, 글꼴 · 크기 · 색 · 위치 · 배경 상자 스타일, 영상에 입히기 또는 .srt 저장 |
| 앱 정보 | `설정 → 앱 정보`: 앱 이름 · 버전 · 개인정보 · `MIT License · © parkrye` · `새 버전 받기` · `오픈소스 라이선스` |

### 단축키

| 키 | 동작 |
|---|---|
| `Ctrl+Shift+F9` | 녹화 시작 / 중지 (어디서나, 설정에서 변경) |
| `Ctrl+Shift+F10` | 일시정지 / 계속 (어디서나, 설정에서 변경) |
| 미리보기에서 드래그 | 소스 이동 · 크기 조절 (Shift: 비율 무시, Alt: 자석 정렬 끄기, 방향키: 1px 이동) |
| 편집기 `Space` / `S` / `Delete` | 재생 · 정지 / 재생 위치에서 자르기 / 구간 삭제 |
| 편집기 `Alt+←` `Alt+→` | 선택한 구간을 앞 · 뒤로 |
| 편집기 `E` | 선택한 구간의 효과 (속도 · 음높이 · 페이드 · 볼륨 · 화면 · 전환) |
| 편집기 `C` / `I` / `G` | 화면 캡처 / 이미지 넣기 / 빈 구간 넣기 |
| 편집기 휠 | 미리보기 · 타임라인 확대 (타임라인 `Shift+휠`: 좌우 이동) |
| 편집기 `T` / `[` / `]` | 자막 추가 / 자막 시작 · 끝을 재생 위치로 |
| 편집기 `Ctrl+Z` / `Ctrl+Y` / `Ctrl+S` | 되돌리기 / 다시하기 / 자막 저장 |
| 편집기 `Ctrl+Shift+S` | 편집 프로젝트 저장 |

### 저장 위치

| 무엇 | 어디 |
|---|---|
| 녹화 파일 | `동영상\EasyDoStudio\` (설정에서 변경) |
| 장면 · 소스 · 설정 | `%AppData%\EasyDoStudio\project.json` |
| 자막 | 영상과 같은 폴더, 같은 이름의 `.srt` |
| 편집 중 캡처 | 영상과 같은 폴더의 `영상이름_캡처\` |
| 자막 생성 모델 | `%LocalAppData%\EasyDoStudio\models\` |

## 개인정보

광고 없음 · 수집 · 전송 없음. 계정 · 사용 통계 · 오류 보고도 없습니다. 녹화 · 편집 파일과 설정은 이 PC에만 저장합니다.

인터넷은 자막 자동 생성을 처음 쓸 때 음성 인식 모델(whisper.cpp ggml, 약 550MB)을 [Hugging Face](https://huggingface.co/ggerganov/whisper.cpp)에서 받을 때만 씁니다. 음성 인식은 PC 안에서 처리하며 오디오를 밖으로 보내지 않습니다.

## EasyDo 시리즈

| 앱 | 용도 | 플랫폼 |
|---|---|---|
| [EasyDoDraw](https://github.com/parkrye/MultiProject_EasyDoDraw) | 그림 · 애니메이션 | Android · Windows |
| [EasyDoWrite](https://github.com/parkrye/AppProject_EasyDoWrite) | 소설 · 글쓰기 | Android |
| [EasyDoRead](https://github.com/parkrye/AppProject_EasyDoRead) | 책 · 문서 읽기 | Android |
| [EasyDoShelve](https://github.com/parkrye/AppProject_EasyDoShelve) | 웹 소설 서재 | Android |
| [EasyDoPhoto](https://github.com/parkrye/AppProject_EasyDoPhoto) | 카메라 · 사진 편집 | Android |
| [EasyDoDiet](https://github.com/parkrye/AppProject_EasyDoDiet) | 식단 · 운동 기록 | Android |
| [EasyDoZip](https://github.com/parkrye/AppProject_EasyDoZip) | 파일 · 압축 관리 | Android |
| [EasyDoGame](https://github.com/parkrye/AppProject_EasyDoGame) | 미니 게임 모음 | Android |
| [EasyDoMix](https://github.com/parkrye/AppProject_EasyDoMix) | 영상 · 오디오 편집 | Android |
| [EasyDoRecord](https://github.com/parkrye/AppProject_EasyDoRecord) | 녹음 | Android |
| [EasyDoStudio](https://github.com/parkrye/DesktopProject_EasyDoStudio) | 화면 녹화 · 영상 편집 | Windows |

버그 · 제안은 [Issues](https://github.com/parkrye/DesktopProject_EasyDoStudio/issues)에 남겨 주세요.

## 라이선스

MIT License · © parkrye

포함된 라이브러리와 외부 구성 요소 고지는 앱 안 `설정 → 앱 정보 → 오픈소스 라이선스`에서 볼 수 있습니다.

| 이름 | 용도 | 라이선스 |
|---|---|---|
| [NAudio](https://github.com/naudio/NAudio) | 오디오 캡처 · 재생 (exe에 포함) | MIT |
| [Vortice.Windows](https://github.com/amerkoleci/Vortice.Windows) | Direct3D 11 화면 합성 (exe에 포함) | MIT |
| [FFmpeg](https://ffmpeg.org/) | 인코딩 · 디코딩 · 자막 입히기 · 음성 인식 (따로 설치, 포함하지 않음) | LGPL / GPL |
| [whisper.cpp](https://github.com/ggerganov/whisper.cpp) 모델 | 자막 자동 생성 (처음 사용 시 다운로드) | MIT |
