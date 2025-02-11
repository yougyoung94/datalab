## 제공 데이터
핸즈온 데이터는 여성쇼핑몰을 한 번에 모아주는 필수 앱 <a href="https://www.notion.so/croquis/a561a88ad03e4022860924fd557a0da3" target="_blank">지그재그</a>에서 제공하였습니다.

https://docs.google.com/document/d/137sbTTov-c6IoD8uDeVpPKvnubYf83XIjJLPBumrl58/mobilebasic

### 항목
- 지그재그 앱 이용자 로그
- 이용자 정보 (id, OS, 연령)
- 쇼핑몰 정보 (쇼핑몰 명, 카테고리, 연령, 스타일)
- 상품 정보 (상품 id, 대분류 카테고리, 가격, 상품 이미지 종류, 이미지 사이즈)
- 이용자 수: 10,000명
- 쇼핑몰 수: 200개
- 상품 수 : 위의 쇼핑몰 상품 중 유저와의 액션이 발생한 모든 상품
- 데이터 제공 영역 : 상품 검색, 쇼핑몰 랭킹, 즐겨찾기, 카테고리 검색, 내 상품

### 단위
- 금액: KRW
- 시간: KST
- 이미지 너비, 높이: Pixel

## 데이터 명세
### user_event_logs.csv: 지그재그의 이벤트로그 정보
|Name          |Description         |Remark                                                                                                                                                                                                       |
|--------------|--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|timestamp     |이벤트 발생 시간|                                                                                                                                                                                                            |
|user_id       |이용자 고유 식별자          |                                                                                                                                                                                                            |
|event_origin  |이벤트가 발생한 앱 위치       |goods_search_result: 특정 검색어의 상품 검색 결과 (i.e. goods_search_result/반팔티) <br>shops_ranking: 쇼핑몰 랭킹 영역 <br>shops_bookmark: 즐겨찾기 영역 <br>category_search_result: 카테고리 검색 결과 (i.e. category_search_result/상의) <br>my_goods: 내 상품' 영역|
|event_name    |발생한 이벤트 명           |app_page_view: 앱 내 화면 이동 <br>enter_browser: 앱 내 클릭을 통해, 특정 웹페이지로 진입 <br>add_bookmark: 특정 쇼핑몰을 즐겨찾기 추가 <br>remove_bookmark: 특정 쇼핑몰을 즐겨찾기 제거 <br>add_my_goods: 특정 상품을 내 상품 추가 <br>remove_my_goods: 특정 상품을 내 상품 제거                 |
|event_goods_id|이벤트가 발생한 상품 고유 식별자  |상품 관련 이벤트가 아닌 경우 공백                                                                                                                                                                                         |
|event_shop_id |이벤트가 발생한 쇼핑몰 고유 식별자 |쇼핑몰 관련 이벤트가 아닌 경우 공백                                                                                                                                                                                        |
### order_info.csv: 지그재그의 주문 정보
|Name          |Description         |Remark                                                                                                                                                                                                       |
|--------------|--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|timestamp     |상품 주문 발생 시간   |                                                                                                                                                                                                            |
|user_id       |이용자 고유 식별자          |                                                                                                                                                                                                            |
|goods_id      |주문한 상품의 고유 식별자      |                                                                                                                                                                                                            |
|shop_id       |주문한 쇼핑몰의 고유 식별자     |                                                                                                                                                                                                            |
|price         |상품주문금액       |                                                                                                                                                                                                            |

### user_info.csv: 지그재그의 이용자 정보
|Name          |Description         |Remark                                                                                                                                                                                                       |
|--------------|--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|user_id       |이용자 고유 식별자   |                                                                                                                                                                                                            |
|os            |이용자의 기기 OS          |                                                                                                                                                                                                            |
|age           |이용자가입력한연령   |- 범위: 15~45 <br>- 값이 45인 경우 45세 이상을 의미 - 값이 '-1' 인 경우 결측을의미                                                                                                                                                    |

### shop_info.csv: 지그재그에 입점한 쇼핑몰 정보
|Name          |Description         |Remark                                                                                                                                                                                                       |
|--------------|--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|shop_id       |쇼핑몰 고유 식별자   |                                                                                                                                                                                                            |
|name          |쇼핑몰명|                                                                                                                                                                                                            |
|category      |쇼핑몰이 등록한 카테고리       |'의류', '가방', '슈즈', '란제리&파자마', '액세서리', '비치웨어', '빅사이즈', '커플룩', '피트니스', '임부복', '패션소품'                                                                                                                           |
|age           |쇼핑몰의 등록한 연령대        |- category 값이 '의류'인 경우 age값 존재 (그 외의 경우 공백) <br>- '10대', '20대 초반', '20대 중반', '20대 후반', '30대 초반', '30대 중반', '30대 후반' 값 중 최대 3가지 값을 연속으로 가질 수 있음 <br>- 연속되는값의구분자: '/'                                                |
|style         |쇼핑몰이 등록한 스타일        |1. category 값이 '의류', '빅사이즈', '커플룩', '액세서리'인 경우 style 값 존재 (그 외의 경우 공백)  <br>2. category 별 가질 수 있는 style 값 <br>- 의류: '페미닌', '모던시크', '심플베이직', '러블리', '유니크', '미시스타일', '캠퍼스룩', '빈티지', '섹시글램', '스쿨룩', '로맨틱', '오피스룩', '럭셔리', '헐리웃스타일' 중 최대 2가지 값을 가질 수 있음 <br>- 연속되는 값의 구분자: '/' <br>- 빅사이즈, 커플룩: 의류영역 style 중 1가지 값을 가질수 있음 <br>- 액세서리: '페미닌', '심플시크', '키치', '펑키', '큐티', '볼드&에스닉' 중 1가지 값을 가질 수 있음|


### goods_info.csv: 지그재그에 등록 된 상품 정보
|Name          |Description         |Remark                                                                                                                                                                                                       |
|--------------|--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|goods_id      |상품 고유 식별자 |                                                                                                                                                                                                            |
|timestamp     |마지막 상품 정보 업데이트 시간|                                                                                                                                                                                                            |
|shop_id       |쇼핑몰 고유 식별자          |                                                                                                                                                                                                            |
|category      |상품의 카테고리            |'상의', '바지', '스커트', '원피스', '비치웨어', '아우터', '악세사리', '슈즈', '가방', '패션소품', '피트니스', '란제리&파자마' 중 1가지 값을 가질 수 있음                                                                                                     |
|price         |상품의 가격      |상품에서 제공하는 옵션에 따라 실제 이용자에게 적용되는 가격은 다를 수 있음                                                                                                                                                                  |
|image_type    |상품 대표 이미지의 확장자      |'jpg', 'gif', 'png' 값을 가질 수 있음                                                                                                                                                                              |
|image_width   |상품 대표 이미지의 너비|                                                                                                                                                                                                            |
|image_height  |상품 대표 이미지의 높이|                                                                                                                                                                                                            |
