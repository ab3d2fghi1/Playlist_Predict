# Playlist_Predict
사용자 선호도 기반 음악 예측
</br>

### 1. 데이터 수집
#### (1) Spotify API
> <img src="https://github.com/ab3d2fghi1/Playlist_Predict/assets/104991721/e08158a6-d94c-4caf-b3ce-f5b690e68277" width="30%" height="20%"></img>
>
> [Spotify for Developers](https://developer.spotify.com/) 사이트에서 제공되는 API를 이용하여 audio features 추출
> 
> <img src="https://github.com/ab3d2fghi1/Playlist_Predict/assets/104991721/1688ee28-cfd7-4a7f-9286-094af19fbc11" width="50%" height="40%"></img>
>
> disliked(50) + liked(100) = 150 -> 총 150개의 음원 정보 수집

#### (2) Lyrics
> 해당 음원 가사 수집
</br>

### 2. 데이터 전처리
#### (1) Tabular Data 변수 선택
> <img src="https://github.com/ab3d2fghi1/Playlist_Predict/assets/104991721/78189963-dad7-434c-9a5e-641809205ca1" width="30%" height="20%"></img>
>
> 필요한 변수만 추출

#### (2) Text Data W2V
> gensim.models.Word2Vec 라이브러리 활용한 W2V

#### (3) OverSampling
> <img src="https://github.com/ab3d2fghi1/Playlist_Predict/assets/104991721/0edb24cb-c9ea-49c3-b5c2-63b30baa97a1" width="40%" height="30%"></img>
>
> 클래스 불균형 ->  데이터 증강을 통한 불균형 해소
> 
> ##### (3.1) Tabular Data - SVMSMOTE
> > <img src="https://github.com/ab3d2fghi1/Playlist_Predict/assets/104991721/03f3b455-0543-4e25-ae32-b2c7f3998e3d" width="40%" height="30%"></img>
> >
> > SVMSMOTE 모델을 이용한 데이터 증강
> ##### (3.2) Text Data - Back Translation
> > 역번역을 이용한 데이터 증강
> > 
> > googletrans API를 이용한 역번역 시행
> >
>
> * OverSampling 결과
> 
> <img src="https://github.com/ab3d2fghi1/Playlist_Predict/assets/104991721/f57cb339-590a-4672-ad66-5604369a2736" width="40%" height="30%"></img>
</br>

### 3. ML 모델링
#### 1. RidgeClassifier
> 규제 선형 모델, 과적합 방지를 위한 회귀 계수 패널티 부여

#### 2. LinearDiscriminantAnalysis
> 가정을 위배하더라도 성능이 비교적 안정적

</br>

### 4. 추후 보완 사항
#### 1. 과적합
> 과적합 발생
>
> -> 전처리 방식의 보완을 통한 문제 해결

#### 2. 데이터 증강
> 적은 데이터 수
>
> -> 원본 데이터의 성질을 해치지 않는 방식의 데이터 증강 기법 적용을 통한 성능 향상 기대

#### 3. NLP Model
> 언어모델 활용을 통한 성능 향상 기대
