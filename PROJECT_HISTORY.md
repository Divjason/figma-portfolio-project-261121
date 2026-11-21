# MoviePick PROJECT HISTORY

MoviePick의 사용자 이해부터 제품 결정까지 단계별 진행과 결과를 기록한다.

## STEP 01 — UX 리서치 계획

- 일자: 2026-11-21
- 역할: UX Researcher
- 상태: 완료
- 산출물: [research/01_research_plan.md](research/01_research_plan.md)

### 진행 내용

사용자 리서치 자료가 없는 상태에서 페르소나 제작을 위한 탐색 조사를 설계했다. 제품 범위는 영화 검색, 상세 정보 확인, 관심 영화 저장으로 두었다.

1. 페르소나에 채울 항목을 기본 프로필, 이용 맥락, 목표, 탐색 행동, 의사결정 기준, 정보 니즈, 저장 동기, 경험 평가, 마찰과 기대, 대표 시나리오로 고정했다.
2. 리서치 목적 3개(RO-01–RO-03)를 탐색 경로, 선택·저장 이유, 경험 수준으로 정의했다.
3. 객관식 8문항과 5점 척도 4문항으로 설문 SQ-01–SQ-12를 작성했다.
4. 개방형 인터뷰 IQ-01–IQ-08을 작성하고, 문항마다 페르소나 항목을 연결했다.
5. 수집 후 분석 목적 AP-01–AP-03을 유형 분류, 니즈 정리, 경험 해석의 순서로 정의했다.

### 결과

- 리서치 목적: RO-01 탐색 행동과 이용 맥락, RO-02 선택 기준·정보 니즈·저장 동기, RO-03 경험 수준과 상황적 차이.
- 설문 12문항: 빈도, 기기, 상황, 시작 행동, 선택 기준, 확인 정보, 저장 빈도, 저장 이유, 탐색 용이성, 정보 충분성, 저장 재접근, 선택 확신.
- 인터뷰 8질문: 최근 탐색 과정, 목표, 정보 선택의 이유, 저장 방식, 저장 이후 확인, 잘 된 순간과 예상과 다른 순간, 현재 방식을 유지하는 이유, 세 기능을 이어서 쓰는 하루.
- 분석은 설문으로 유형과 분포를 만들고, 인터뷰 인용이 함께 있을 때만 페르소나 문장으로 확정한다.

### 주요 결정

- 조사 대상은 MoviePick 사용자가 아니라 최근 3개월 안에 볼 영화를 직접 찾아 본 사람이다.
- 특정 불편이 있다고 가정하는 유도 문항은 넣지 않았다. 척도는 용이성, 충분성, 재접근, 확신을 긍정 문장으로 측정한다.
- 저장하지 않는 응답은 결측이 아니다. SQ-08의 “저장하지 않는다”와 SQ-11의 “해당 없음”으로 분리한다.
- 이번 단계에서는 페르소나 프로필과 기능 요구사항을 만들지 않는다.

### 다음 단계

설문 배포와 인터뷰 진행 후, AP-01–AP-03 순서로 페르소나 항목을 채운다.

## STEP 01-b — Google Form 제작

- 일자: 2026-11-21
- 역할: UX Researcher
- 상태: 차단
- 사용 도구: Google Forms MCP `create_complete_form`, `create_form`

### 진행 내용

`research/01_research_plan.md`의 SQ-01–SQ-12로 Form 생성을 시도했다. `create_complete_form`과 `create_form` 모두 Google API 500 Internal error를 반환했다.

Drive API로 같은 서비스 계정을 확인한 결과는 다음과 같다.

- 계정: `figmamcp@figma-portfolio-261114.iam.gserviceaccount.com`
- 저장 용량 한도: 0
- 공유 드라이브: 없음
- 파일 생성: 403 `storageQuotaExceeded`
- 편집 가능한 기존 설문지 `1xiD-sAUZZE93RWUf4Wbrv6wB0nwOLFjHhRl7c5Znsfs`는 강의 만족도 문항이 있어 재사용하지 않음

### 결과

MoviePick 설문 Form은 생성되지 않았다. 서비스 계정은 공유된 파일만 수정할 수 있고, 새 Form의 소유자가 될 수 없다.

### 재개 조건

빈 Google Form을 만든 뒤 `figmamcp@figma-portfolio-261114.iam.gserviceaccount.com`에 편집자로 공유한다. 공유된 Form ID로 제목, 설명, SQ-01–SQ-12를 넣는다. SQ-09, SQ-10, SQ-12는 1–5 선형 척도, SQ-11은 해당 없음 보기가 필요해 단일 선택, SQ-05와 SQ-06은 체크박스다.

## STEP 02 — 합성 리서치 데이터

- 일자: 2026-11-21
- 역할: UX Research Data Simulation
- 상태: 완료
- 산출물: [data/moviepick_survey_120.csv](data/moviepick_survey_120.csv), [data/moviepick_interview_8.csv](data/moviepick_interview_8.csv), [data/moviepick_data_dictionary.md](data/moviepick_data_dictionary.md), [research/02_synthetic_data.md](research/02_synthetic_data.md)

### 진행 내용

STEP 01의 SQ-01–SQ-12와 IQ-01–IQ-08에 맞춰 교육용 합성 응답을 만들었다. 모집과 응답 수집은 하지 않았다. 생성 시드는 20261121이다.

1. 검색, 둘러보기, 순위·신작, 저장 재사용, 주변 추천, 즉시 시청·외부 메모의 잠재 유형을 먼저 배정하고, 시작 행동·저장·경험 점수가 함께 움직이게 했다. 유형 이름은 CSV에 넣지 않았다.
2. 연령 6개 구간, 직업 12개, 서비스 이용 습관 5개를 합성 프로필로 부여했다. 이 세 필드는 설문 문항이 아니다.
3. 비저장 응답은 SQ-08 “저장하지 않는다”와 SQ-11 “해당 없음(저장하지 않음)”으로 두고, 저장 목록으로 시작하는 응답은 자주 또는 대부분 저장으로 맞췄다.
4. 설문 120명 가운데 8명을 지정해 IQ-01–IQ-08 답변을 설문 행과 맞게 작성했다. 높은 동의와 항목별 낮은 동의를 모두 넣었다.
5. 저장한 CSV를 다시 읽어 건수, 누락, 중복 ID, 보기 문자열, 문항 간 규칙을 검증했다.

### 결과

- 합성 설문 120행. ID `S001`–`S120`. 중복 `respondent_id` 0. 누락 셀 0.
- 합성 인터뷰 8명, 답변 64행. ID `I001`–`I008`. 각 참여자의 `respondent_id`가 설문에 있다. 누락 셀 0.
- SQ-11 “해당 없음(저장하지 않음)” 40건은 비저장 40명과 일치하는 응답 코드다.
- 높은 동의(SQ-09와 SQ-12가 모두 4 이상) 48명, 하나 이상의 항목이 1–2인 응답 68명. 두 기준이 겹치는 응답은 13명이다.
- 객관식 보기와 인터뷰 질문 문장은 STEP 01과 일치하고, 정합성 규칙 위반은 0건이다.

### 주요 결정

- 데이터는 교육용 합성 데이터로 표기한다. 현장 조사 결과로 다루지 않는다.
- 연령, 직업, 서비스 이용 습관은 다양성을 위한 프로필 필드다. SQ 번호는 붙이지 않는다.
- 낮은 척도 점수는 불편의 원인으로 단정하지 않는다. 분포와 인터뷰의 상황 서술로 남긴다.
- STEP 01 문서와 STEP 01-b 기록은 수정하지 않는다.

### 다음 단계

이 합성 응답으로 AP-01–AP-03 순서에 따라 페르소나 항목을 채운다. 설문 패턴과 인터뷰 인용이 둘 다 있을 때만 페르소나 문장으로 확정한다.

## STEP 03 — 합성 데이터 저장

- 일자: 2026-11-21
- 역할: Data Manager
- 상태: 완료
- 사용 도구: Google Sheets MCP `gsheets_read_range`, `gsheets_update_range`
- 산출물: [research/03_data_storage.md](research/03_data_storage.md)
- 스프레드시트: [MoviePick_UX_Research_Week03](https://docs.google.com/spreadsheets/d/1iQCc7aH4rHSpFdaWH8HEOp3BVIq_VToTSwauCs0U-XI/edit)

### 진행 내용

STEP 02의 교육용 합성 설문 120건과 인터뷰 64행을 Google Sheets에 저장하고, MCP로 다시 읽어 원본 CSV와 대조했다. 원본 CSV는 수정하지 않았다.

1. 서비스 계정은 새 스프레드시트를 만들 수 없다. `spreadsheets.create`는 403 PERMISSION_DENIED, 파일 복사는 403 `storageQuotaExceeded`다. Drive 용량 한도는 0이다.
2. 값이 비어 있던 공유 스프레드시트 `figma-portfolio_261121`의 제목을 `MoviePick_UX_Research_Week03`으로 바꿨다. `시트1`을 삭제하고 Survey_Raw, Interview_Raw, Data_Dictionary를 만들었다.
3. 1행은 컬럼명으로 두고 `respondent_id`를 유지했다. 설문·인터뷰의 마지막 열 `data_nature`에 `교육용 합성 데이터`를 넣어 합성 데이터임을 표시했다.
4. 값은 RAW로 기록했다. 사전 시트의 메타 행 7개 `position`은 MCP `gsheets_update_range`로 `—`를 기록했다.
5. MCP `gsheets_read_range`로 세 시트를 다시 읽어 셀 단위로 비교했다.

### 결과

- Survey_Raw 120행, 17열, 2,057셀. `S001`–`S120`. CSV 16열과 불일치 0. 빈 셀 0.
- Interview_Raw 64행, 6열, 390셀. `I001`–`I008`, 참여자당 IQ-01–IQ-08. 설문 `respondent_id` 연결 불일치 0. 빈 셀 0.
- Data_Dictionary 30행, 7열, 217셀. 메타 7행, 설문 컬럼 17행, 인터뷰 컬럼 6행. 빈 셀 0.
- 모든 데이터 행의 `data_nature`는 `교육용 합성 데이터`다.

### 주요 결정

- 새 파일을 만들지 못하고, 비어 있던 공유 스프레드시트의 제목을 바꿔 사용했다.
- 합성 데이터 표기는 CSV를 바꾸지 않고 시트 컬럼 `data_nature`와 사전 메타 행에 둔다.
- `해당 없음(저장하지 않음)`은 빈칸이 아닌 응답 코드로 저장한다.
- STEP 01, STEP 01-b, STEP 02 기록과 원본 CSV는 수정하지 않는다.

### 다음 단계

저장된 합성 응답으로 AP-01–AP-03 순서에 따라 페르소나 항목을 채운다. 설문 패턴과 인터뷰 인용이 둘 다 있을 때만 페르소나 문장으로 확정한다.

## STEP 04 — 접속 가능한 Form에 설문 양식 제작

- 일자: 2026-11-21
- 역할: UX Researcher
- 상태: 완료
- 사용 도구: Google Forms MCP `get_form`, `delete_question`, `update_form_info`, `add_choice_question`, `add_scale_question`
- Form ID: `1xiD-sAUZZE93RWUf4Wbrv6wB0nwOLFjHhRl7c5Znsfs`
- 응답 링크: https://docs.google.com/forms/d/e/1FAIpQLSeVIFBomR9AtQUDydBxPdwXMS-FRiJm2ME76CinetMTdMMZmQ/viewform
- 편집 링크: https://docs.google.com/forms/d/1xiD-sAUZZE93RWUf4Wbrv6wB0nwOLFjHhRl7c5Znsfs/edit

### 진행 내용

서비스 계정이 새 Form을 만들 수 없어, 편집 권한이 있는 기존 Form에 연결했다. 강의 만족도 문항 4개를 삭제한 뒤 제목과 설명을 바꾸고 SQ-01–SQ-12를 추가했다. 응답 받기를 켰다.

### 결과

- 제목: MoviePick 영화 탐색 경험 설문
- 문항 12개, 모두 필수
- SQ-01–SQ-04, SQ-07, SQ-08: 단일 선택
- SQ-05, SQ-06: 체크박스. 안내는 최대 3개이며, Forms API는 개수 제한을 저장하지 못한다.
- SQ-09, SQ-10, SQ-12: 1–5 선형 척도. 앵커는 전혀 아니다 / 매우 그렇다.
- SQ-11: 1–5 문구에 `해당 없음 (저장하지 않음)`을 붙인 단일 선택. 선형 척도에는 해당 없음을 넣을 수 없다.

### 주요 결정

- 새 Form 생성은 다시 시도하지 않고, 접속 가능한 Form을 MoviePick 설문으로 교체했다.
- STEP 01의 문항 문장과 보기를 유지했다.

## STEP 05 — 합성 리서치 분석

- 일자: 2026-11-21
- 역할: UX Research Analyst
- 상태: 완료
- 사용 도구: Google Sheets MCP `gsheets_read_range`
- 산출물: [research/04_research_analysis.md](research/04_research_analysis.md)
- 스프레드시트: [MoviePick_UX_Research_Week03](https://docs.google.com/spreadsheets/d/1iQCc7aH4rHSpFdaWH8HEOp3BVIq_VToTSwauCs0U-XI/edit)

리서치 문서 번호는 04다. 히스토리의 STEP 04는 설문 양식 제작으로 이미 기록되어 있어, 이번 분석은 STEP 05로 잇는다.

### 진행 내용

Survey_Raw 120행과 Interview_Raw 64행을 읽어 AP-01, AP-02, AP-03 순서로 집계했다. 비율에는 건수와 분모를 붙였고, 정량 분포와 인터뷰 발화를 나누어 적었다. 대표 유형은 시작 행동이 서로 겹치지 않고 설문 패턴과 인터뷰 발화가 함께 있는 3개로 제한했다.

### 결과

- 주 1회 이상 탐색은 61/120이다. 20대는 27/36, 40대는 6/22, 50대는 3/12, 60대 이상은 2/8이다.
- 기기는 스마트폰 58/120이다. 서비스 브랜드 이름은 없고, 합성 프로필상 OTT 한 곳 41/120, 여러 OTT 37/120이다.
- 확인 정보는 줄거리 요약 69/120, 예고편 47/120이 많다. 자투리 시간 20명 중 19명은 러닝타임을 선택 기준으로 골랐다.
- 낮은 동의는 항목마다 시작 행동이 다르다. 둘러보기 26명 중 탐색 용이성 1–2점은 15명, 순위·신작 24명 중 정보 충분성 1–2점은 14명, 저장 목록으로 시작하는 16명 중 재접근 1–2점은 12명이다.
- 앱에 저장하는 응답은 80/120, 저장하지 않거나 다른 곳에 메모하는 응답은 40/120이다. 재접근 1–2점은 저장 응답 80명 중 22명이다.
- 인터뷰 8명 중 5명은 저장 이유가 제목과 함께 남기를 말했다. 3명은 함께 보는 상황에 맞는 등급·시간·언어·후기를 확인한다.
- 대표 유형 3개: 이름 검색 40명, 장르·분위기 둘러보기 26명, 저장 목록 재사용 16명. 각 유형에 Behavior, Needs, Pain Points, Goals와 근거를 적었다.

### 주요 결정

- 데이터에 있는 값만 집계했다. 현장 조사 결과로 쓰지 않는다.
- 척도 1–2점은 동의 분포로 남기고, 상황 서술은 인터뷰 문장에 있는 내용만 Pain Points에 넣었다.
- 순위·신작 24명과 주변 추천 14명은 대표 유형 카드로 올리지 않고 건수와 인터뷰 연결만 남겼다.
- STEP 01, STEP 02, STEP 03 문서와 원본 CSV는 수정하지 않는다.

### 다음 단계

세 유형의 근거 표를 기준으로 페르소나 프로필 문장과 대표 시나리오를 쓸 수 있다. 화면 요구사항은 아직 만들지 않았다.

## STEP 06 — 페르소나 정의

- 일자: 2026-11-21
- 역할: UX Strategist, Persona Designer
- 상태: 완료
- 사용 도구: Notion MCP `notion-create-pages`, `notion-update-page`
- 산출물: [research/05_persona_definition.md](research/05_persona_definition.md)
- Notion: [MoviePick / 07. Persona](https://app.notion.com/p/41fa44c22fe381c88e9bef51ce71b817)

리서치 문서 번호는 05다. Notion 페이지 제목은 요청된 이름 `MoviePick / 07. Persona`다. 페이지는 비공개 초안으로 만들었고, 부모 페이지는 지정하지 않았다.

### 진행 내용

STEP 05 분석의 대표 유형 3개 가운데 하나를 골라, 합성 응답 한 명을 행동 앵커로 두고 가상 프로필을 덮었다. 화면 요구사항은 만들지 않았다.

1. 유형 B, 장르·분위기 목록을 둘러보며 비교하는 응답 26/120을 골랐다. 탐색, 비교, 저장, 재방문이 I002의 시간 순서 안에 있고, 탐색 용이성 1–2점이 15/26, 선택 확신 1–2점이 13/26이다.
2. 페르소나는 26명의 평균이 아니다. 낮은 동의 쪽인 S041 / I002에 고정했다. 같은 유형의 I007(동의 5, 4, 5, 5)은 합치지 않았다.
3. 가상 이름은 서지안, 가상 나이는 34세다. 직업은 S041의 합성 프로필인 프리랜서다. 취미는 데이터에 없어 가상으로만 적고 행동 근거로 쓰지 않았다.
4. 시나리오는 검색, 비교, 저장, 재방문 순이다. 검색은 제목 검색이 아니라 장르·분위기 목록을 훑는 단계로 정의했다.
5. Motive, Goal, Problem을 각 4개 적고, 항목마다 I002의 합성 인터뷰 기록과 설문 분포를 붙였다. 성향 점수와 숙련도 수치는 만들지 않았다. 서비스 브랜드 이름은 적지 않았다.

### 결과

- 페르소나: 서지안, 34세, 프리랜서. 한 달에 1–3회, 노트북, 혼자, 여러 OTT.
- 앵커 척도 SQ-09, SQ-10, SQ-11, SQ-12는 2, 3, 3, 2다. 성격 점수가 아니다.
- Markdown과 Notion의 유형 선정, 프로필, 시나리오, Motive, Goal, Problem, Personality, Skill, Favorite Apps가 같다.

### 주요 결정

- 인원이 더 많은 유형 A(40명) 대신 유형 B를 골랐다. 선정 기준은 인원수가 아니라, 요청된 네 단계가 한 인터뷰에 있고 낮은 동의가 그 시작 행동에 몰린 점이다.
- 이름, 만 나이, 취미는 가상 설정이다. 영화 행동은 합성 인터뷰 기록에만 근거한다.
- 재구성 문장과 합성 인터뷰 기록을 문서 안에서 구분했다. 현장 발화로 적지 않는다.
- I002의 문제를 26명 전체의 원인으로 확정하지 않는다.
- 이전 STEP의 리서치 문서와 원본 CSV는 수정하지 않는다.

### 다음 단계

이 페르소나로 화면 요구사항을 쓸 수 있다. 이번 단계에서는 만들지 않았다. Notion 페이지는 비공개 초안이다. 부모 페이지를 지정하면 그쪽으로 옮긴다.

## STEP 07 — Figma Persona 슬라이드

- 일자: 2026-11-21
- 역할: UX/UI Portfolio Designer
- 상태: 완료
- 사용 도구: Figma MCP `create_session`, `get_libraries`, `get_metadata`, `search_design_system`, `use_figma`, `generate_image`, `get_screenshot`
- 산출물: [research/06_figma_persona.md](research/06_figma_persona.md)
- Figma: [07 / PERSONA](https://www.figma.com/design/EQDKMNij5zyhELswY1Mne8/261107---figma_tutor?node-id=2098-24)

리서치 문서 번호는 06이다. 히스토리의 STEP 06은 페르소나 정의로 이미 기록되어 있어, 이번 슬라이드 제작은 STEP 07로 잇는다.

### 진행 내용

STEP 06의 가상 페르소나 서지안을 기존 MoviePick 포트폴리오 파일에 새 슬라이드로 옮겼다. 화면 요구사항은 만들지 않았다.

1. 파일 `EQDKMNij5zyhELswY1Mne8`의 기존 `07 / PERSONA` (`2059:44`)는 다른 가상 인물이라 수정하지 않았다. 페이지 `07_persona_research`를 추가하고 프레임 `07 / PERSONA` (`2098:24`, 1920×1080)를 만들었다.
2. 구독 라이브러리는 0개였다. 외부 UI 키트와 테스트 라이브러리의 heading 스타일은 이 파일의 네이비 톤과 달라 가져오지 않았다. 배경, 카드, 본문, 시안은 로컬 페인트 스타일을 썼다.
3. 구조는 레퍼런스 `07.persona.png`의 구역을 따랐다. 정렬과 간격은 기존 07 프레임의 왼쪽 헤더, 패딩 40/72/28/72, 간격 16, 카드 모서리 12를 따랐다.
4. 성향 막대, 숙련도 퍼센트, OTT 브랜드 로고는 넣지 않았다. 페르소나 문서가 점수와 브랜드 이름을 만들지 않기 때문이다. Personality와 Skill은 문장 행이고, Favorite Apps는 습관 범주 세 개다.
5. 교육용 합성 데이터라는 표기를 헤더, 프로필 배지, 푸터에 넣었다. 인용은 I002 IQ-02이고, 시나리오는 재구성이라고 적었다.

### 결과

- 프레임: `07_persona_research` / `07 / PERSONA` (`2098:24`)
- 링크: https://www.figma.com/design/EQDKMNij5zyhELswY1Mne8/261107---figma_tutor?node-id=2098-24
- 인물: 서지안, 34세, 프리랜서. 앵커 S041 / I002. 유형 B 26/120.
- 반복 행은 `Research Persona/` 컴포넌트 인스턴스다. 보드는 슬라이드 아래 y=1240이다.
- 기존 프레임 `2059:44`의 제목은 변경 전과 같다.

### 주요 결정

- 인원이 더 많은 유형이 아니라, STEP 06에서 고정한 I002만 슬라이드에 올렸다. I007은 합치지 않았다.
- 레퍼런스의 막대와 브랜드 로고는 데이터에 없는 점수로 읽히므로 문장과 범주로 바꿨다.
- 이름, 만 나이, 취미, 초상은 가상이다. 초상의 성별은 설문에 없어 행동 근거로 쓰지 않는다.
- 이전 STEP의 리서치 문서와 원본 CSV, 기존 01–10 프레임은 수정하지 않는다.

### 다음 단계

이 페르소나로 화면 요구사항을 쓸 수 있다. 이번 단계에서는 만들지 않았다. 새 슬라이드는 `01~10` 개요 보드에 복제하지 않았다.

## STEP 08 — 사용자 여정 계획

- 일자: 2026-11-21
- 역할: UX Researcher
- 상태: 완료
- 사용 도구: Notion MCP `notion-fetch`
- 산출물: [research/07_journey_plan.md](research/07_journey_plan.md)
- Notion 참고: [MoviePick / 07. Persona](https://app.notion.com/p/41fa44c22fe381c88e9bef51ce71b817)

리서치 문서 번호는 07이다. 히스토리의 STEP 07은 Figma Persona 슬라이드다. 이번 여정 계획은 STEP 08로 잇는다. 슬라이드 `08 / USER JOURNEY MAP`은 이번 단계에서 만들지 않았다.

### 진행 내용

문서 05와 Notion Persona가 같은 앵커인지 확인한 뒤, 서지안의 기록된 순서를 요청된 네 단계에 배치했다. 화면 요구사항은 만들지 않았다.

1. Notion `MoviePick / 07. Persona`의 앵커, Motive, Goal, Problem이 문서 05와 같은지 대조했다. 앵커는 S041 / I002, 유형 B 26/120이다.
2. 영화 탐색, 검색 결과 확인, 상세 정보 확인, 관심 영화 저장의 목적, 주요 행동, 관찰 항목을 표로 적었다.
3. 이 페르소나의 검색 결과는 제목 검색 결과가 아니라 장르·분위기 목록이다. IQ-01의 시간 순서를 따랐다. 줄거리와 예고를 본 뒤 다른 앱의 같은 장르 목록으로 돌아온다.
4. 재방문은 IQ-05의 기록이라 네 단계 밖에 두었다. 화면 이름, 조작 횟수, 시간, 메모 칸의 존재는 가설 H1–H7로 표시했다.

### 결과

- 여정의 인물은 서지안이다. 행동은 S041 / I002에만 고정했다. I007은 합치지 않았다.
- 1단계 목적은 제목 없이 그 밤의 감정 조건을 정하고 드라마 목록을 여는 것이다. 행동은 B1이다.
- 2단계 목적은 포스터 톤이 가까운 후보를 목록에서 가리는 것이다. 세 편을 고르고, 인기 작품이 반복된다. 상세 뒤에 다른 앱 목록으로 돌아온다.
- 3단계 목적은 줄거리 분위기와 예고 색이 같은 결인지 확인하는 것이다. 평점 숫자는 거의 보지 않고, 긴 러닝타임은 빼며, 포스터와 줄거리가 다르면 후보를 바꾼다.
- 4단계 목적은 한 편으로 정하지 못한 후보를 나중에 비교하려고 남기는 것이다. 남은 둘 중 한 편만 저장하고, 그날은 재생하지 않으며, 이유는 적지 않는다.
- G3은 재생 이후의 목표라 네 단계 안에서 이루어진 상태로 적지 않았다. G4와 M4는 기대다.

### 주요 결정

- 인원이 더 많은 유형이 아니라, STEP 06에서 고정한 I002만 여정에 올렸다.
- 문서 05의 재방문은 다섯 번째 단계로 올리지 않았다. 저장 행동의 결과로 7장에 남겼다.
- 데이터에 없는 정렬, 필터, 클릭 수, 감정 곡선, 브랜드 이름은 사실로 적지 않고 가설로 두었다.
- 이전 STEP의 리서치 문서와 원본 CSV, Figma 프레임은 수정하지 않는다.

### 다음 단계

이 계획으로 `08 / USER JOURNEY MAP` 슬라이드를 그릴 수 있다. 이번 단계에서는 만들지 않았다. 가설 H1–H7은 화면 요구사항으로 바꾸지 않았다.

## STEP 09 — Playwright 여정 검증

- 일자: 2026-11-21
- 역할: UX Usability Tester
- 상태: 로그아웃 경로 완료. 로그인 후 저장 확인은 차단
- 사용 도구: Playwright MCP `browser_navigate`, `browser_snapshot`, `browser_click`, `browser_type`, `browser_take_screenshot`, `browser_evaluate`, `browser_network_requests`
- 산출물: [research/08_playwright_journey.md](research/08_playwright_journey.md)
- 화면 증거: [research/08_screenshots](research/08_screenshots)
- 대상: https://moviepick-web.vercel.app/
- 기준: [research/07_journey_plan.md](research/07_journey_plan.md)

리서치 문서 번호는 08이다. 히스토리의 STEP 08은 사용자 여정 계획이다. 이번 화면 검증은 STEP 09로 잇는다.

### 진행 내용

문서 07의 네 단계를 MoviePick 홈에서 확인했다. 뷰포트는 1440×900으로 지정했다. 계정이 필요해진 저장 성공 경로는 계정을 만들지 않고 멈췄다.

1. 홈을 열었다. 상태 문구는 `인기 영화를 살펴보세요.`이고 영화 카드는 19장이었다. `nav`, 장르, 분위기, 필터, 정렬 컨트롤은 없었다.
2. `기생충`을 검색했다. 주소는 그대로였고 카드 4장이 나왔다. 상태 문구는 `검색 완료`였다.
3. `기생충`의 `상세`를 눌렀다. 같은 페이지에 줄거리, 개봉일 `2019-05-30`, 평점 `8.5`가 열렸다. 장르와 러닝타임은 화면 밖이었다. 같은 영화의 상세 응답에는 장르 코미디·스릴러·드라마와 runtime 131이 있었다. 클릭 기록 요청은 503이었고, 상태 문구에 MySQL 호스트 오류가 나왔다.
4. 인기 목록에서 `오디세이` 상세는 카드 아래에 붙었다. 제목의 viewport top은 1683px, 뷰포트 높이는 900px이라 스크롤 전에는 보이지 않았다. `상세 닫기`는 블록을 없앴다.
5. 로그인하지 않고 `♡ 저장`을 눌렀다. 상태는 `즐겨찾기를 사용하려면 로그인하세요.`이고 즐겨찾기는 0이었다. `localStorage`와 `sessionStorage`는 비어 있었다.
6. 빈 회원가입은 422 `Anonymous sign-ins are disabled`, 빈 로그인은 400 `missing email or phone`이었다. 입력값은 넣지 않았고 계정은 만들지 않았다.
7. `드라마` 검색은 화면 20장, 응답 `total_results` 32와 `total_pages` 2였다. 다음 페이지 컨트롤은 없었다. `zzzznotamovie999`는 카드 0장인데 상태 문구는 `검색 완료`였다. 통계 새로고침은 `GET /stats/popular` 503이었다.

### 결과

- 제목 검색과 같은 페이지의 상세 열기, 상세 닫기, 제목 클릭으로 인기 목록 복귀는 동작했다.
- 상세 화면에 보이는 정보는 줄거리, 개봉일, 평점이다. 응답에 있던 장르와 러닝타임은 `기생충` 상세 블록에 그려지지 않았다.
- 관심 영화 저장은 로그아웃 상태에서 목록에 반영되지 않았다. 로그인 후 저장 목록은 확인하지 못했다.
- 문서 07의 장르·분위기 목록을 여는 1단계 행동은 해당 메뉴가 홈에 없어 수행하지 못했다.

### 주요 결정

- 빈 인증 버튼이 서버 오류를 반환한 뒤에도 이메일과 비밀번호를 넣어 가입하지 않았다.
- 자동화 결과로 포스터 톤, 확신, 감정을 단정하지 않았다.
- 응답 본문에만 있고 화면에 없는 값은 화면 정보로 적지 않고 응답 확인으로 나누었다.
- 가설 H1–H7은 화면 요구사항으로 바꾸지 않았다. 이전 STEP의 리서치 문서와 원본 CSV, Figma 프레임은 수정하지 않는다.

### 다음 단계

로그인된 테스트 계정이 있으면 저장 성공과 즐겨찾기 목록 반영을 이어서 확인한다. 이번 단계에서는 계정을 만들지 않았다. `08 / USER JOURNEY MAP` 슬라이드도 만들지 않았다.

## STEP 10 — Firecrawl 여정 콘텐츠

- 일자: 2026-11-21
- 역할: UX Content & Information Architecture Analyst
- 상태: 공개 화면 추출 완료. 로그인 후 저장 화면은 미추출
- 사용 도구: Firecrawl MCP `firecrawl_map`, `firecrawl_scrape`
- 산출물: [research/09_firecrawl_journey.md](research/09_firecrawl_journey.md)
- 대상: https://moviepick-web.vercel.app/
- 기준: [research/08_playwright_journey.md](research/08_playwright_journey.md)

리서치 문서 번호는 09다. 히스토리의 STEP 09는 Playwright 여정 검증이다. 이번 콘텐츠 추출은 STEP 10으로 잇는다.

### 진행 내용

Firecrawl로 공개 화면의 문구와 컨트롤을 추출했다. 계정이 필요한 저장 성공 화면은 계정을 만들지 않고 한계로 남겼다. 문서 08과 이전 리서치 문서는 수정하지 않았다.

1. 사이트 맵에는 루트 URL 하나만 있었다. `/movies/496243`과 `/favorites`는 HTTP 404였다.
2. 홈은 상태 `인기 영화를 살펴보세요.`와 영화 카드 19장이다. 카드는 포스터, 제목, 점수, 날짜, `상세`, `♡ 저장`이다. 같은 주소에 즐겨찾기, 영화관 찾기, 클릭 통계가 있다.
3. `기생충` 검색은 주소가 그대로인 카드 4장이고 상태는 `검색 완료`다. `드라마`는 카드 20장이고 페이지 이동 버튼이 없다. `zzzznotamovie999`는 카드 0장인데 상태 문구는 같다.
4. `기생충` 상세는 같은 페이지의 줄거리, `개봉일: 2019-05-30 / 평점: 8.5`, `상세 닫기`다. 상태 문구는 MySQL 호스트 오류다.
5. 로그아웃 상태에서 `♡ 저장`을 누르면 `즐겨찾기를 사용하려면 로그인하세요.`이고 즐겨찾기는 `(0)`이다.

### 결과

- 검색, 상세, 즐겨찾기는 별도 문서 주소가 아니다. 상세와 즐겨찾기 경로는 404다.
- 상세 블록에서 확인한 정보는 제목, 라벨 없는 줄거리, 개봉일, 평점이다.
- 관심 영화의 저장 완료 목록은 로그인 전 화면에 없다.
- 문서 08과 같은 조작의 화면 문구는 충돌하지 않았다. API 총 건수, 상세 응답 본문, 스크롤 좌표, 빈 인증 오류, 통계 503은 이번 호출에서 다시 추출하지 않았다.

### 주요 결정

- Markdown에 없는 입력값은 DOM value로만 적었다. 영화관 입력값은 `수원 영화관`, 반경 선택 텍스트는 `5km`다.
- 응답 본문에만 있을 수 있는 장르와 러닝타임은 화면에 라벨이 없으면 화면 정보로 적지 않았다.
- 문서 08에만 있고 이번에 조작하지 않은 항목은 충돌이 아니라 미추출로 두었다.
- 이전 STEP의 리서치 문서와 원본 CSV, Figma 프레임은 수정하지 않는다.

### 다음 단계

로그인된 테스트 계정이 있으면 저장 성공과 즐겨찾기 목록을 이어서 확인한다. 이번 단계에서는 계정을 만들지 않았다.

## STEP 11 — 사용자 여정 분석

- 일자: 2026-11-21
- 역할: UX Research Data Analyst
- 상태: 완료. 로그인 후 저장 성공은 미확인
- 사용 도구: Google Sheets MCP `gsheets_update_range`, `gsheets_read_range`. 빈 탭 추가는 Sheets API `batchUpdate` `addSheet`
- 산출물: [research/10_journey_analysis.md](research/10_journey_analysis.md)
- 시트: [MoviePick_User_Journey](https://docs.google.com/spreadsheets/d/1iQCc7aH4rHSpFdaWH8HEOp3BVIq_VToTSwauCs0U-XI/edit#gid=1545377464)
- 기준: [research/07_journey_plan.md](research/07_journey_plan.md), [research/08_playwright_journey.md](research/08_playwright_journey.md), [research/09_firecrawl_journey.md](research/09_firecrawl_journey.md)

리서치 문서 번호는 10이다. 히스토리의 STEP 10은 Firecrawl 여정 콘텐츠다. 이번 여정 분석은 STEP 11로 잇는다.

### 진행 내용

문서 07의 네 단계에 합성 인터뷰 I002와 MoviePick 공개 화면 관찰을 나란히 두었다. 감정 점수는 측정값이 없어 가설과 목표 예시로만 적었다.

1. 각 단계를 합성 경로와 화면 관찰로 나누고, Doing, Thinking, Pain Point, Evidence를 적었다. 화면 층의 Thinking은 비워 두었다.
2. AS-IS는 합성 발화에 대응시킨 감정 가설과, 화면에서 과제 마찰을 본 가설로 분리했다. 두 점수는 평균하지 않았다.
3. TO-BE는 네 단계 모두 목표 예시 4다. 눈금 5는 수집한 목표 점수가 없어 쓰지 않았다. SQ-09–SQ-12는 인접 동의로만 병기했다.
4. 재방문은 IQ-05 각주로 남겼다. P3, P4는 저장 직후 감정으로 옮기지 않았다.
5. 기존 스프레드시트에 탭 `MoviePick_User_Journey`를 추가했다. MCP에는 탭 생성 도구가 없어 빈 탭만 API로 만들었고, 값은 `gsheets_update_range`로 기록한 뒤 `gsheets_read_range`로 `A1:M9`, `A11:C28`을 다시 읽었다.

### 결과

- 합성 AS-IS 가설은 1단계 2, 2단계 2, 3단계 2, 4단계 3이다. 4단계 3은 저장 직후 감정 문장이 없어 신뢰가 낮다.
- 화면 AS-IS 과제 마찰 가설은 1단계 2, 2단계 2, 3단계 2, 4단계 1이다. 4단계 1은 로그아웃 경로에서 저장이 목록에 반영되지 않은 범위다.
- TO-BE 목표 예시는 네 단계 모두 4다.
- 홈에는 장르·분위기 목록이 없다. 상세 블록에는 줄거리, 개봉일, 평점이 있고 예고, 장르, 러닝타임, 유사 작품 문구는 없다. 로그아웃 저장은 로그인 안내로 끝난다.
- 문서 08과 문서 09가 같은 조작의 화면 문구를 적은 항목은 충돌하지 않았다.

### 주요 결정

- I002의 여정을 유형 B 26명 또는 MoviePick 세션의 감정으로 일반화하지 않았다.
- 설문 동의 2, 3, 3, 2를 단계 감정 점수로 환산하지 않았다. 4단계 합성 가설 3은 SQ-11의 3점과 숫자가 같을 뿐 같은 점수가 아니다.
- 응답 본문에만 있는 장르와 러닝타임은 화면 정보로 세지 않았다.
- 가설 H1–H7은 화면 요구사항으로 바꾸지 않았다. 이전 STEP의 리서치 문서와 원본 CSV, Figma 프레임, 기존 세 시트는 수정하지 않는다.

### 다음 단계

로그인된 테스트 계정이 있으면 저장 성공과 즐겨찾기 목록을 이어서 확인한다. 이번 단계에서는 계정을 만들지 않았다. `08 / USER JOURNEY MAP` 슬라이드도 만들지 않았다.
