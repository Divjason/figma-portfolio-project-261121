# MoviePick STEP 03 — 합성 데이터 저장

- 프로젝트: MoviePick
- 역할: Data Manager
- 단계: STEP 03. 설문 120건과 인터뷰 8명분의 Google Sheets 저장
- 작성일: 2026-11-21
- 상태: 저장 및 재조회 검증 완료
- 데이터 성격: 교육용 합성 데이터
- 기준 설계: [research/01_research_plan.md](01_research_plan.md)
- 원본 데이터: [research/02_synthetic_data.md](02_synthetic_data.md)

## 1. 작업 목적

STEP 02의 합성 설문 120건과 인터뷰 64행을 Google Sheets에 두고, 저장 결과를 다시 읽어 누락이 없는지 확인한다.

이번 단계의 산출물은 스프레드시트 3개 시트와 이 저장 기록이다. 원본 CSV는 수정하지 않는다. 페르소나 문장과 분석은 만들지 않는다.

## 2. 스프레드시트

| 항목 | 값 |
| --- | --- |
| 제목 | MoviePick_UX_Research_Week03 |
| URL | https://docs.google.com/spreadsheets/d/1iQCc7aH4rHSpFdaWH8HEOp3BVIq_VToTSwauCs0U-XI/edit |
| 스프레드시트 ID | `1iQCc7aH4rHSpFdaWH8HEOp3BVIq_VToTSwauCs0U-XI` |
| 시트 | Survey_Raw, Interview_Raw, Data_Dictionary |

Google Sheets MCP에는 스프레드시트를 새로 만드는 도구가 없다. 같은 서비스 계정으로 `spreadsheets.create`를 호출하면 403 PERMISSION_DENIED가 반환되고, 파일 복사는 403 `storageQuotaExceeded`가 반환된다. 서비스 계정 Drive 용량 한도는 0이다. STEP 01-b와 같은 제약이다.

편집 가능한 파일은 공유된 스프레드시트 하나뿐이었고, 시트 `시트1`의 값은 비어 있었다. 이전 제목은 `figma-portfolio_261121`이다. 이 파일의 제목을 `MoviePick_UX_Research_Week03`으로 바꾸고, `시트1`을 삭제한 뒤 세 시트를 추가했다.

## 3. 저장 내용

원본은 [data/moviepick_survey_120.csv](../data/moviepick_survey_120.csv), [data/moviepick_interview_8.csv](../data/moviepick_interview_8.csv), [data/moviepick_data_dictionary.md](../data/moviepick_data_dictionary.md)다. CSV 파일은 변경하지 않았다.

1. 각 시트의 1행은 컬럼명이다.
2. 설문과 인터뷰의 `respondent_id`는 CSV 값을 그대로 두었다. 설문 ID는 `S001`–`S120`이다.
3. 설문·인터뷰 데이터 행의 마지막 컬럼 `data_nature` 값은 모두 `교육용 합성 데이터`다. 이 컬럼은 CSV에 없고, 시트에서 합성 데이터임을 표시하기 위해 붙였다.
4. 값은 `RAW`로 기록해 숫자와 문장이 해석되어 바뀌지 않게 했다.
5. Data_Dictionary는 데이터셋 메타 7행, Survey_Raw 컬럼 17행, Interview_Raw 컬럼 6행이다. 메타 행의 `position`은 컬럼 순서가 없음을 `—`로 적었다.

## 4. 시트별 건수

건수는 헤더를 뺀 데이터 행이다. 셀 수는 헤더를 포함한다.

| 시트 | 데이터 행 | 열 | 셀 | 내용 |
| --- | --- | --- | --- | --- |
| Survey_Raw | 120 | 17 | 2,057 | 응답자 1명 = 1행. CSV 16열과 `data_nature` |
| Interview_Raw | 64 | 6 | 390 | 참여자 8명 × 질문 8개. CSV 5열과 `data_nature` |
| Data_Dictionary | 30 | 7 | 217 | 메타 7행, 설문 컬럼 17행, 인터뷰 컬럼 6행 |

## 5. 검증 결과

저장 직후 Google Sheets MCP `gsheets_read_range`로 세 시트를 다시 읽었다. 설문은 `Survey_Raw!A1:Q121`, 인터뷰는 `Interview_Raw!A1:F65`, 사전은 `Data_Dictionary!A1:G31`이다. 다시 읽은 값을 STEP 02 CSV 및 기록한 사전 행과 셀 단위로 비교했다.

| 검사 | 결과 |
| --- | --- |
| Survey_Raw 데이터 행 | 120 |
| Survey_Raw 열 | 17. 1행 컬럼명, 마지막 열 `data_nature` |
| 설문 ID | `S001`–`S120`, 결번 없음 |
| 중복 `respondent_id` | 0 |
| 설문 원본 16열과 CSV 불일치 | 0 |
| 설문 빈 셀 | 0 |
| Interview_Raw 데이터 행 | 64 |
| 인터뷰 참여자 | `I001`–`I008` |
| 참여자당 질문 | IQ-01–IQ-08 각 1개 |
| 인터뷰 `respondent_id` 연결 | I001=S017, I002=S041, I003=S062, I004=S008, I005=S096, I006=S055, I007=S073, I008=S112 |
| 인터뷰 ID가 설문에 없음 | 0 |
| 인터뷰 원본 5열과 CSV 불일치 | 0 |
| 인터뷰 빈 셀 | 0 |
| `data_nature`가 `교육용 합성 데이터`가 아닌 데이터 행 | 0 |
| Data_Dictionary 데이터 행 | 30 |
| Data_Dictionary 빈 셀 | 0 |
| 원본 CSV 수정 | 없음 |

SQ-11의 `해당 없음(저장하지 않음)`은 빈칸이 아닌 응답 코드로 저장되어 있다.

## 6. 이번 단계에서 하지 않은 일

- 원본 CSV와 STEP 01·STEP 02 문서 수정
- AP-01–AP-03 분석과 페르소나 문장
- 새 Google Drive 파일 생성. 서비스 계정 용량 한도가 0이라 기존 공유 스프레드시트의 제목을 바꿨다.

다음은 이 시트에 저장된 합성 응답으로 AP-01, AP-02, AP-03 순서에 따라 페르소나 항목을 채우는 단계다.
