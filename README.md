# crunch price homework

## 문제 정의
검색했을때 원하는 상품이 나오지 않는 이슈 해결책 찾기입니다
추정되는 원인으로는

1. 검색어가 "상품명"만 보기 때문에
2. 상품의 카테고리값이 정확하지 않기 때문에
3. 그외 또 다른 원인

결과 도출을 "소비자들이 원하는 상품을 찾을수 있도록 검색결과의 정확도를 높임"으로 정했을때 어떤 경로/방법으로 해결할 수 있을지 고민해서 알려주세요
 
## 해결 과정

### 토큰 분석
crunch price 상품중 카테고리 정보가 등록되지 않은 상품이 많이 있습니다.<br>
또한 상품 "**[코카콜라]미닛메이드 망고 175mL x 30캔[도매퍼스트]**"과 같은 상품의 경우 "음료수" 로 검색했을때 검색 결과에 노출되지 않습니다.<br>
http://www.crunchprice.com/goods/goods_view.php?goodsNo=1000284206

이를 해결 하고자
1. konlpy의 twitter tokennizer를 사용하여 상품명에서 명사만 추출
1. 추출한 명사를 네이버 쇼핑에 검색하여 검색결과 목록에서 카테고리 정보만 크롤링
1. 크롤링한 카테고리중 출현빈도가 높은 3개의 카테고리 추출하여 저장
1. 크롤링한 카테고리중 출현빈도가 높은 10개의 카테고리를 토큰으로 분리하여 출현빈도가 높은 3개를 키워드로 저장

위의 과정을 통해 대부분 상품의 카테고리를 찾을 수 있었습니다.
https://github.com/dooyeoung/crunch_price_homework/blob/master/2.%20%EC%B9%B4%ED%85%8C%EA%B3%A0%EB%A6%AC%20%ED%81%AC%EB%A1%A4%EB%A7%81.ipynb

### 이미지 분석
상품명에 포함되지 않는 키워드를 찾기 위해 상품이미지를 google vision 서비스로 분석하여 누락된 키워드를 추출하였습니다.
https://github.com/dooyeoung/crunch_price_homework/blob/master/4.%20%EC%9D%B4%EB%AF%B8%EC%A7%80%20%EB%9D%BC%EB%B2%A8%20%EC%B6%94%EC%B6%9C.ipynb
