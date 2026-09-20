# 갤창랭킹 v2.1.0

디시인사이드(DCInside) 갤러리의 게시글 데이터를 크롤링하여 갤러들의 활동 순위(갤창랭킹)를 집계하는 Windows GUI 프로그램입니다.

> **Note**: 본 프로젝트는 [hanel2527](https://github.com/hanel2527) 님의 `dcinisde-crawler.ver.2`를 기반으로, 최신 디시인사이드 차단 우회 및 버그 패치를 적용한 유지보수 버전입니다.
> 
> - **Original Author**: hanel2527
> - **Maintainer / Updated by**: [SlausonArch](https://github.com/SlausonArch)

---

## 🚀 다운로드
최신 실행 파일은 아래 릴리즈 링크에서 다운로드하실 수 있습니다:
### 👉 [갤창랭킹 최신 버전 다운로드 (Releases)](https://github.com/SlausonArch/dcinisde-crawler-2026/releases)

---

## 🛠️ v2.1.0 패치 내역 (2026.09)

- **디시인사이드 503 오류(서버 사용할 수 없음) 해결**:
  - 디시인사이드 서버의 봇/크롤러 차단에 대응하여 브라우저 `User-Agent` 및 `Accept` 헤더, gzip 자동 압축 해제를 전송하는 `DcWebClient` 구현
  - 연속 크롤링 시 `WebClient` 헤더 초기화로 인한 503 재발 현상 해결
- **보안 프로토콜(TLS 1.2) 지원**:
  - .NET Framework 환경에서 HTTPS 통신 시 TLS 1.2 보안 프로토콜을 명시적으로 활성화
- **프로그램 안정성 및 예외 처리 강화**:
  - 갤러리 확인 및 크롤링 중 네트워크 오류 발생 시 프로그램이 비정상 종료(크래시)되지 않도록 예외 처리 추가
  - GitHub 원시(Raw) 파일 기반으로 버전 확인 로직 개선
- **빌드 및 호환성 개선**:
  - 프로젝트 내 라이브러리 참조 경로 개선 및 VS Code 빌드/디버그 태스크(`tasks.json`, `launch.json`) 추가

---

## 📌 주요 기능

- **직관적인 GUI**: Windows Forms 기반 데스크톱 애플리케이션
- **유연한 수집 기준**: 페이지 범위 또는 날짜 범위 지정 크롤링
- **중복 방지**: 동일 게시글 중복 카운팅 방지
- **동일 갤러 자동 병합**:
  - 통신사 IP(통피) 식별, 동일 닉네임 유동 및 동일 아이디 고정닉 자동 병합
  - 수동 병합 기능 지원
- **다양한 저장 포맷**:
  - 텍스트 파일(`.txt`) 저장
  - 디시인사이드 게시글용 HTML 표(`<table>`) 형식 저장

---

## 💻 실행 환경 및 요구사항

- **운영체제**: Windows 7 / 8 / 10 / 11
- **런타임**: [.NET Framework 4.6.1](https://dotnet.microsoft.com/download/dotnet-framework/net461) 이상
- **외부 종속 라이브러리**:
  - HtmlAgilityPack (v1.11.9)
  - Newtonsoft.Json (v12.0.2)

---

## 📖 사용 방법

### 1. 갤러리 정보 입력 및 크롤링
![use01.png](./img/use01.png)
1. **갤 ID 입력**: `https://gall.dcinside.com/board/lists?id=programming` 의 경우 `programming` 입력 (마이너 갤러리는 '마이너 갤러리' 체크)
2. **페이지 또는 날짜 설정**: 시작 페이지 및 끝 페이지(또는 날짜 범위) 지정
3. **갤창랭킹 시작** 클릭

![use02.png](./img/use02.png)
4. 크롤링 진행 후 완료 메시지 및 순위 요약 확인

---

### 2. 데이터 불러오기 및 동일 갤러 합치기
![use03.png](./img/use03.png)
5. **데이터 목록 불러오기** 클릭 후 수집된 데이터 파일(`갤id_연월일_시분초.json`) 선택

![use04.png](./img/use04.png)
6. **동일 갤러 자동 처리** 클릭: 동일 고닉 및 유동 닉네임이 자동으로 합쳐집니다.
7. 자동 처리되지 않은 사용자는 체크박스 선택 후 **동일 갤러 합치기**를 클릭하여 수동 병합 가능

---

### 3. 결과 파일 저장 및 디시 글 작성
![use06.png](./img/use06.png)
8. **파일 저장** 선택:
   - **텍스트 파일로 저장**: 일반 텍스트 형식으로 저장
   - **표로 저장**: 디시 글쓰기에 바로 넣을 수 있는 HTML 테이블 형식으로 저장

![use07.png](./img/use07.png)
9. 저장된 결과물은 프로그램 폴더 내 `results` 폴더에 생성됩니다.

![use08.png](./img/use08.png)
![use09.png](./img/use09.png)

10. **디시인사이드에 올리는 법**:
    - HTML 파일 내용 복사
    - 갤러리 글쓰기 화면 우측 상단의 **HTML 체크박스** 활성화 후 붙여넣기
    - HTML 체크 해제 시 표가 깔끔하게 렌더링됩니다.

![use10.png](./img/use10.png)

---

## ⚖️ 라이선스 (License)

This project is licensed under the **Apache License 2.0**.
자세한 내용은 [LICENSE](./LICENSE) 파일을 참고하시기 바랍니다.

```
Copyright (c) 2019 hanel2527
Copyright (c) 2026 SlausonArch

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0
```
