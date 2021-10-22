# python 환경설정

## python

### 인터프리터 설치
- 파이썬은 파이썬 언어를 해석할 수 있는 인터프리터라는 프로그램을 설치하여 사용한다.
- 인터프리터란 소스코드를 읽고 해석하여 수행하는 프로그램이다.
- Cpytho, jython, iornpython, Skulpt 등의 파이썬 종류가 있다.

### 아나콘다 설치 후 실행
- 인터프리터 외에 다양한 패키지와 개발도구를 제공하는 배포판이 있다. 파이썬 표준 배포판은 Anaconda
- www.anaconda.com/distribution 에서 아나콘다 설치
- 프롬프트에서 ipython 치면 바로 python 사용가능
-스크립트 실행
   - New -> TextFile -> 코드 작성 -> .py 저장. 아나콘다 프롬프트 열고 python test.py 입력하면 실행

### 쥬피터 노트북 설치 후 실행
- 웹 브라우저를 사용하여 문서와 코드를 동시에 지원하는 개발도구
- 웹 서버 형태로 구현되어 있다.
- REPL 방식 : 읽고 Read, 실행하고 Evaluation, 보여주고 Print, 반복 Loop 한다.
- 스크립트 방식은 REPL 이 아니라 전체 코드를 실행하면 결과만 나온다.

### 다양한 패키지
- 다른 프로그램 제작에 사용하기 위해 미리 만들어진 프로그램 집합 라이브러리 또는 패키지라고 한다.
- 아나콘다 배포판 설치하면 기본 패키지 같이 설치된다. 대부분 패키지는 직접 설치.
- 파이썬 패키지는 pypi.ort 라는 공식패키지 서버에 등록된다. 아나콘다는 anaconda.org 라는 독자적인 패키지 서버가 있다.
- 패키지 관리자 : 파이썬은 pip, 아나콘다는 conda
- 아나콘다 패키지 관리자가 패키지간의 의존성 관리 성능이 뛰어나다.
- 패키지 설치할때는 conda 로 설치하는 게 좋다.
- 설치 명령
```
pip install 패키지이름
conda install 패키지이름
```
### 데이터분석용 파이썬 패키지들

#### 1) Numpy
- 수치해석, 선형대수 계산, 다차원 배열 클래스, 벡터화 연산 지원
- 수치해석 라이브러리
- www.numpy.org

#### 2) Scipy
- 고급수학 함수, 수치적 미적분, 미분방정식 계산, 최적화, 신호 처리 지원
- 과학기술 함수 라이브러리
- www.scipy.org

#### 3) Sympy
- 인수 분해, 미분, 적분 등 심볼릭 연산 지원
- 심볼릭 연산 라이브러리
- www.sympy.org

#### 4) Pandas
- 테이블 형태의 데이터를 다루는 프레임 자료형 제공, 자료탐색, 자료정리에 유용
- 데이터분석 라이브러리
- https://pandas.pydata.org/

#### 5) Matplotlib
- 각종 그래프, 챠트 지원
- 시각화 라이브러리
- https://matplotlib.org/

#### 6) Seaborn
- 고급통계차트 지원
- 시각화 라이브러리
- http://seaborn.pydata.org/

#### 7) StatsModels
- 통계, 회귀분석, 시계열 분석 지원
- 통계 및 회귀분석, 시계열 분석 라이브러리
- www.StatsModels.org

#### 8) Scikit-Learn
- 머신러닝 학습용 패키지, 머시러닝 모형 제공
- 머신러닝 라이브러리
- https://scikit-learn.org/stable/

#### 9) TensorFlow
- 신경망 모형,심볼릭 연산, 그래프 연산 모형 등 제공
- 딥러닝 라이브러리 (저)
- www.tensorflow.org

#### 10) Keras
- 인공싱경망 구현, 백엔드 엔진으로 텐서플로우 사용
- 딥러닝 라이브러리 (고)
- https://keras.io/

#### 11) PyTorch
- 딥러닝 라이브러리 Torch 기반의 딥러닝 개발 지원
- 딥러닝 라이브러리
- https://pytorch.org/

#### 12) pgmpy
- 확률론적 그래프 모형 구현 라이브러리
- http://pgmpy.org/

## matplotlib font 설정확인
- 맷플랏립에서 사용할 수 있는 폰트를 리스트로 반환 해준다.
- 새로운 폰트를 설치하고 맷플랏립에서 사용할 수 있다.
```
import matplotlib

[f.name for f in matplotlib.font_manager.fontManager.ttflist if f.name.startswith('N')]
```
```
['Nanum Pen Script',
 'Nirmala UI',
 'NanumGothic',
 'NanumGothic',
 'NanumBarunGothic',
 'New Gulim',
 'NanumBarunGothic',
 'NanumSquare',
 'Niagara Engraved',
 'Nirmala UI',
 'NanumGothic',
 'NanumSquareRound',
 'NanumBarunGothic',
 'NanumSquare',
 'NanumBarunpen',
 'NanumBarunGothic',
 'NanumSquare',
 'NanumGothic',
 'NanumSquareRound',
 'NanumMyeongjo',
 'NanumSquareRound',
 'Nirmala UI',
 'NanumMyeongjo',
 'NanumSquare',
 'Nanum Brush Script',
 'NanumBarunpen',
 'NanumSquareRound',
 'NanumMyeongjo',
 'Niagara Solid']
```

## matplotlib font 설정하는 방법 
- ipython_config.py 파일에서 아래 해당하는 부분에 실행 명령어를 넣는다.
```
## lines of code to run at IPython startup.
#c = get_config()
#c.InteractiveShellApp.exec_lines = [
#    "mpl.rc('font', family='Malgun Gothic')",  #  맑은고딕 폰트 사용
#    "mpl.rc('font', family='NanumGothic')"   # 나눔고딕 폰트 사용
#    "mpl.rc('axes', unicode_minus=False)", # 유니코드 음수 기호 사용
#    "mpl.rc('figure', figsize=(8, 5))",  # 그림 크기 (단위: 인치)
#    "mpl.rc('figure', dpi=300)",  # 그림 해상도
#]
```

## 스타트업 파일 설정하는 방법
- 아이파이썬이나 쥬피터 노트북을 이용한 콘솔이 시작되기전에 실행되는 파일.
- 스타트업 디렉토리안에 파이썬 스크립트 파일 형태로 저장하면 된다.
- 스타트업 파일 이름에 따른 우선순위 : 00.py -> 01.py -> ... -> 50.py -> ... -> 99.py
- 00.py 파일 만들고 아래내용 복붙

```
## 경고 무시
#import warnings
#warnings.simplefilter('ignore')
#
## 자주 사용하는 패키지를 임포트
#import matplotlib as mpl
#import matplotlib.pylab as plt
#from mpl_toolkits.mplot3d import Axes3D
#import seaborn as sns
#import numpy as np
#import scipy as sp
#import pandas as pd
#import statsmodels.api as sm
#import sklearn as sk
#
#
## matplotlib 설정
#mpl.use('Agg')
#
## seaborn 설정
#sns.set()
#sns.set_style("whitegrid")
#sns.set_color_codes()
#
```

## python 버전관리 하는 방법 (연구 필요) !!! 중요
- python 의 버전과 사용하는 패키지의 버전이 맞지 않으면 실행 안됨.
- python 버전도 계속 업그레이드 되고 있기 떄문에 무작정 버전업을 하면 이전에 설치한 다른 패키지들과 버전이 맞지 않아서 실행이 안될 수 있음.
- 이것을 효율적으로 관리하기 위해서 py env 와 virture env 를 사용하여 파이썬 버전별 가상환경을 구축하는 방법 사용.
- 서버환경을 구축할 떄도 패키지와 파이썬 버전간의 의존성을 잘 따져야 한다. 
