# LinClPass-Releases

린클패스(LinCl Pass) 통합 인증 런처의 **공개 배포 채널**입니다.
소스코드는 비공개이며, 이 repo는 자동 업데이트에 필요한 것만 공개합니다.

## 구성
- **`version.json`** (main 브랜치) — 최신 버전 매니페스트. 런처가 시작 시 이 파일을 읽어
  현재 버전과 비교합니다.
  - `version` — 최신 버전
  - `download_url` — 설치본(Setup.exe) Release 에셋 URL
  - `sha256` — 설치본 무결성 검증 해시
  - `mandatory` — 필수 업데이트 여부
- **Releases** — 각 버전의 설치본(`LinClPassSetup_<ver>.exe`).

## 동작
런처는 시작 시 `version.json`을 확인 → 새 버전이면 안내 → 설치본 다운로드 + SHA256 검증
→ 실행(재설치 + 재시작). 인증서/토큰 불필요(공개 읽기).

## 새 버전 배포 절차
1. `python build/build_installer.py` 로 `LinClPassSetup_<ver>.exe` + `version.json` 생성.
2. 새 태그로 Release 생성 + Setup.exe 업로드.
3. `version.json`의 `download_url`을 새 에셋 URL로 맞춰 main에 커밋.