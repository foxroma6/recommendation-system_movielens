### 분석 데이터 배경
- 데이터셋은 영화 27278개의 20000263 레이팅과 465564의 태깅으로 구성
- 1995년부터 2015년까지 138493의 유저들이 입력한 데이터로 구성
- 각 유저들은 최소 20개의 영화에 대한 레이팅을 진행했음

### 분석 데이터 설명
- 개인 정보 이슈로 인해서 개인 데모 정보는 포함되어 있지 않음
- 모든 유저들은 id로 표현이 되며 그 외의 정보는 제공되지 않음

### 데이터는 총 6가지 테이블로 구성

1. tag.csv: 유저들이 영화마다 적용한 태그 정보

- userId, movieId, tag, timestamp

2. rating.csv : 유저들이 매겨놓은 영화 레이팅 정보

- userId, movieId, rating, timestamp

3. movie.csv: 영화 정보

- movieId, title, genres

4. link.csv: 다른 정보들과 연계해서 분석할 수 있는 매핑 테이블

- movieId, imdbId, tmbdId

5. genome_scores.csv: 태그 정보와 관련된 정보가 들어있는 테이블

- movieId, tagId, relevance

6. genome_tags.csv: 태그 정보 매핑 테이블

- tagId, tag

##### 분석 참고 링크: https://www.kaggle.com/anmol4210/recommendation-system-collaborative-filtering

### Collaborative Filtering 방법론 적용

- 다른 유저의 정보를 사용해서 새로운 유저들에게 아이템을 추천하는 방법
- 비슷한 취향을 가진 유저들을 찾아서 새로운 유저에게 기존에 비슷한 취향을 가진 유저들의 아이템들을 추천
- 머신 러닝 등 다양한 분석 방법론이 있지만, 여기서는 Pearson Correlation Function을 사용할 예정

#### 유저 베이스 추천 시스템의 프로세스
1. 유저를 선정 (본 영화를 베이스로)
2. 영화 레이팅을 기반으로, 가장 유사한 취향을 가진 유저를 찾기
3. 가장 유사한 취향을 가진 유저들이 봤던 영화를 가져오기
4. similarity score 계산
5. similarity score의 점수가 가장 높은 아이템 순으로 추천
