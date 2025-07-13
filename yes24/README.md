# Final Project
- YES24 도서 중 하나의 대분류를 선택하여 데이터를 수집, 정제하고 DRIP 사고 프레임을 적용하여 분석한 결과를 GitHub에 정리하고 발표
- 선택한 대분류: IT 모바일 https://www.yes24.com/Product/Category/Display/001001003
- IT 모바일의 중분류 (019~032)
  - 게임 https://www.yes24.com/product/category/display/001001003027
  - 그래픽/디자인/멀티미디어 https://www.yes24.com/product/category/display/001001003028
  - 네트워크/해킹/보안 https://www.yes24.com/product/category/display/001001003024
  - 모바일 프로그래밍 https://www.yes24.com/product/category/display/001001003023
  - 모바일/태블릿/SNS https://www.yes24.com/product/category/display/001001003021
  - 오피스 활용 https://www.yes24.com/product/category/display/001001003029
  - 웹사이트 https://www.yes24.com/product/category/display/001001003020
  - 인공지능 https://www.yes24.com/product/category/display/001001003032
  - 인터넷 비지니스 https://www.yes24.com/product/category/display/001001003026
  - 컴퓨터 공학 https://www.yes24.com/product/category/display/001001003031
  - 컴퓨터 수험서 https://www.yes24.com/product/category/display/001001003030
  - 컴퓨터 입문/활용 https://www.yes24.com/product/category/display/001001003019
  - 프로그래밍 언어 https://www.yes24.com/product/category/display/001001003022
  - OS/데이터베이스 https://www.yes24.com/product/category/display/001001003025

## Crawling
- Python Selenium 사용
### Crawling 1
- 중분류 별로 '신상품순', '품절포함', '120개씩 보기'를 선택한 후 각 페이지를 html로 저장 (Window, local) \
001001003019/ \
├── 001001003019_page_0001.html \
├── 001001003019_page_0002.html \
├── ... \
└── 001001003019_page_0034.html \
... \
001001003032/ \
├── 001001003032_page_0001.html \
├── 001001003032_page_0002.html \
├── ... \
└── 001001003032_page_0019.html
### Crawling 2
- 위에서 추출한 책 상세 페이지 url로 접속하여 '펼쳐보기'를 모두 누르고 html로 저장 (Ubuntu, server) \
yes24_19/ \
├── 001001003019_01/ (120권의 html 파일 보유) \
│   ├── 133890598.html \
│   ├── ... \
│   └── 146361202.html ... \
└── 001001003019_34/ \
... \
yes24_32/ \
├── 001001003019_01/ \
│   ├── 144689418.html \
│   ├── ... \
│   └── 146361202.html ... \
└── 001001003019_19/

## Parsing 1
### page_html
- Crawling 1의 폴더별로 책의 세부정보를 parsing 후 csv로 저장
  - 001001003???.csv (???에는 중분류 번호: 019~032)
  - 001001003???_log.txt (pasrsing 관련 정보 기록)
 ### book_html
 - Crawling 2의 폴더별로 책의 세부정보를 parsing 후 csv로 저장
   - ITM001001003???.csv (???에는 중분류 번호: 019~032)
   - Parrelel Processing 활용
  
## Presentation
- 전처리
  - 모든 중분류에 대해 아래의 전처리 코드를 실행시킨 후
  - https://sw1kwon.github.io/Capstone1Blog/posts/19.html
  - 중분류 별로 tidy data를 csv로 저장
- 최종 tidy data
  - 위에서 저장한 csv를 아래의 코드를 실행시켜 하나의 tidy data로 합친 후 분석
  - https://sw1kwon.github.io/Capstone1Blog/posts/00.html
- 발표 자료
  - https://sw1kwon.github.io/assets/html/yes24.html
- 한계
  - parsing을 할 때 일관된 기준이 아니라 css와 xpath를 혼용하여 전처리가 매우 복잡해짐
  - 이를 보완하기 위해 css를 우선 기준으로 하는 Parsing 2를 진행
 
## Parsing 2
- code
  - https://sw1kwon.github.io/Capstone1Blog/posts/parsing2.html
### page_html2
- Crawling 1의 폴더별로 책의 세부정보를 parsing 후 csv로 저장
- Parrelel Processing 활용 X
  - 001001003???.csv (???에는 중분류 번호: 019~032)
  - 001001003???_log.txt (parsing 관련 정보 기록)
  - yes24_overall_log.txt (전체 실행 관련 정보 기록)
- Parrelel Processing 활용 O
  - 001001003???_p.csv (???에는 중분류 번호: 019~032)
  - 001001003???_p_log.txt (parsing 관련 정보 기록)
  - yes24_parallel_overall_log.txt (전체 실행 관련 정보 기록)
### book_html2
- Crawling 1의 폴더별로 책의 세부정보를 parsing 후 csv로 저장
- Parrelel Processing 활용 O
  - ITM_001001003??.csv (??에는 중분류 번호: 19~32)
  - yes24_??_log.txt (parsing 관련 정보 기록)
  - yes24_??_error.txt (parsing 되지 않은 파일 정보 기록)
  - yes24_overall_log.txt (전체 실행 관련 정보 기록)

## Appendix
- https://github.com/sw1kwon/yes24-itbook-count
