# 상장법인 감사인 등록제와 생산적 관점의 감사역량 연구 코딩

## Tasks

#### 1] 제출의무자가 회계법인인 감사보고서 F001, F002 제출인명 추출 (./scraper/submitter.py)

DART Scraper는 대상 기간 공시 서류를 다음 단계에 따라 순차적으로 접근하여 단위문서 주소를 찾아서 저장한다.

> lv1. 회사 공시문서 주소 : ./scraper/Dart_Scraper.py 의 Document_Address_Parser 함수로 공시문서 주소 추출  
> lv2. 공시문서 첨부서류 주소 : ./scraper/Dart_Scraper.py 의 Sub_Document_Address_Parser 함수로 첨부서류 주소 추출  
> lv3. 첨부서류 단위문서 주소 : ./scraper/Dart_Scraper.py 의 HTML_Address_Parser 함수로 단위문서 주소 추출

DART Scraper 산출 File명은 위의 세 단계의 계층구조를 반영하고 있다. 예를 들어, "F001_00284240_20201231000514_감사보고서_(2020.09)_20201231000514_2020.12.31_감사보고서_(첨부)재무제표_.html"라는 입수 문서는 다음과 같이 계층구조 식별 정보를 포함하고 있다.

식별정보 | 설명
--- | ---
F001 | 공시문서 타입 (A001 사업보고서, A002 반기보고서, A003 분기보고서, F001 감사보고서, F002 연결감사보고서, F004 회계법인사업보고서. 전체 리스트 DART 오픈API 개발가이드, https://github.com/nKiNk/scrapdart 참조)
00284240 | 감독원 고유번호
20201231000514 | 공시문서 DART 접수번호 : 제출의무자가 DSD 편집기에서 인증서를 이용해 서명한 DRT 파일에 부여된 접수번호
감사보고서 | 공시문서명 (lv1)
(2020.09) | 보고기간 종료월
20201231000514 | 첨부서류 DART 접수번호. 만약, 사업보고서에 첨부된 감사보고서와 같이 공시문서와 첨부서류의 제출의무자가 다른 경우 접수번호가 다를 수 있다.
2020.12.31 | 첨부서류 접수일. 공시서류 접수일과 차이날 수 있다.
감사보고서 | 첨부서류명 (lv2)
(첨부)재무제표 | 단위문서명 (lv3)

위의 DART Scraper 코드 중 lv1의 코드만 분리하면 공시문서 인덱스 단계에서 제출의무자를 추출할 수 있다. 감사보고서 제출의 경우 제출의무자 정보를 추출하면 공시문서 DART 접수번호로 외부감사법에 의한 감사인 정보를 매핑할 수 있다.  


## References

#### A. DART Scraper 사용
