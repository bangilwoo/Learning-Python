---
title: colab에서 kaggle 연결 하기
---   

## install 설치

kaggle에서 파일을 받기 위해서는 colab에 install 설치를 위한 코드를 입력한다.


```python
!pip install kaggle # 느낌표 붙이고(colab에서만), pip install 패키지 이름
```

    Requirement already satisfied: kaggle in /usr/local/lib/python3.6/dist-packages (1.5.9)
    Requirement already satisfied: six>=1.10 in /usr/local/lib/python3.6/dist-packages (from kaggle) (1.15.0)
    Requirement already satisfied: python-dateutil in /usr/local/lib/python3.6/dist-packages (from kaggle) (2.8.1)
    Requirement already satisfied: python-slugify in /usr/local/lib/python3.6/dist-packages (from kaggle) (4.0.1)
    Requirement already satisfied: urllib3 in /usr/local/lib/python3.6/dist-packages (from kaggle) (1.24.3)
    Requirement already satisfied: tqdm in /usr/local/lib/python3.6/dist-packages (from kaggle) (4.41.1)
    Requirement already satisfied: requests in /usr/local/lib/python3.6/dist-packages (from kaggle) (2.23.0)
    Requirement already satisfied: certifi in /usr/local/lib/python3.6/dist-packages (from kaggle) (2020.6.20)
    Requirement already satisfied: slugify in /usr/local/lib/python3.6/dist-packages (from kaggle) (0.0.1)
    Requirement already satisfied: text-unidecode>=1.3 in /usr/local/lib/python3.6/dist-packages (from python-slugify->kaggle) (1.3)
    Requirement already satisfied: idna<3,>=2.5 in /usr/local/lib/python3.6/dist-packages (from requests->kaggle) (2.10)
    Requirement already satisfied: chardet<4,>=3.0.2 in /usr/local/lib/python3.6/dist-packages (from requests->kaggle) (3.0.4)
    

위와 같이 install 설치가 된 것을 확인한다.<br>
설치가 완료 되면 kaggle 방문하여 API파일을 다운 받는다.<br>
- kaggle접속 > Account클릭 > API > Create New API Token클릭

파일 다운을 완료하면 아래의 코드를 실행한다.<br>
실행하고 파일선택을 눌러 kaggle에서 다운 받은 kaggle.json을 선택한다.


```python
from google.colab import files
uploaded = files.upload()
for fn in uploaded.keys():
  print('uploaded file "{name}" with length {length} bytes'.format(
      name=fn, length=len(uploaded[fn])))
  
# kaggle.json을 아래 폴더로 옮긴 뒤, file을 사용할 수 있도록 권한을 부여한다. 
!mkdir -p ~/.kaggle/ && mv kaggle.json ~/.kaggle/ && chmod 600 ~/.kaggle/kaggle.json
```



<input type="file" id="files-cca3b282-96ea-497d-a196-efd561494062" name="files[]" multiple disabled
   style="border:none" />
<output id="result-cca3b282-96ea-497d-a196-efd561494062">
 Upload widget is only available when the cell has been executed in the
 current browser session. Please rerun this cell to enable.
 </output>
 <script src="/nbextensions/google.colab/files.js"></script> 


    Saving kaggle.json to kaggle.json
    uploaded file "kaggle.json" with length 65 bytes
    


```python
ls -1ha ~/.kaggle/kaggle.json
```

    /root/.kaggle/kaggle.json
    

## kaggle 데이터 불러오기

아래와 같이 코드를 입력하면 kaggle에 올라와 있는 파일들을 확인할 수 있다.


```python
!kaggle competitions list # 연동한 kaggle내의 파일 목록을 확인
```

    Warning: Looks like you're using an outdated API Version, please consider updating (server 1.5.9 / client 1.5.4)
    ref                                            deadline             category            reward  teamCount  userHasEntered  
    ---------------------------------------------  -------------------  ---------------  ---------  ---------  --------------  
    contradictory-my-dear-watson                   2030-07-01 23:59:00  Getting Started     Prizes        134           False  
    gan-getting-started                            2030-07-01 23:59:00  Getting Started     Prizes        185           False  
    tpu-getting-started                            2030-06-03 23:59:00  Getting Started  Knowledge        315           False  
    digit-recognizer                               2030-01-01 00:00:00  Getting Started  Knowledge       2356           False  
    titanic                                        2030-01-01 00:00:00  Getting Started  Knowledge      18048            True  
    house-prices-advanced-regression-techniques    2030-01-01 00:00:00  Getting Started  Knowledge       4536            True  
    connectx                                       2030-01-01 00:00:00  Getting Started  Knowledge        390           False  
    nlp-getting-started                            2030-01-01 00:00:00  Getting Started  Knowledge       1184           False  
    rock-paper-scissors                            2021-02-01 23:59:00  Playground          Prizes        149           False  
    riiid-test-answer-prediction                   2021-01-07 23:59:00  Featured          $100,000       1465           False  
    nfl-big-data-bowl-2021                         2021-01-05 23:59:00  Analytics         $100,000          0           False  
    competitive-data-science-predict-future-sales  2020-12-31 23:59:00  Playground           Kudos       9343           False  
    halite-iv-playground-edition                   2020-12-31 23:59:00  Playground       Knowledge         43           False  
    predict-volcanic-eruptions-ingv-oe             2020-12-28 23:59:00  Playground            Swag        193           False  
    hashcode-drone-delivery                        2020-12-14 23:59:00  Playground       Knowledge         79           False  
    cdp-unlocking-climate-solutions                2020-12-02 23:59:00  Analytics          $91,000          0           False  
    lish-moa                                       2020-11-30 23:59:00  Research           $30,000       3395           False  
    google-football                                2020-11-30 23:59:00  Featured            $6,000        916           False  
    conways-reverse-game-of-life-2020              2020-11-30 23:59:00  Playground            Swag        131           False  
    lyft-motion-prediction-autonomous-vehicles     2020-11-25 23:59:00  Featured           $30,000        778           False  
    

목록을 확인해 보고 자신에게 필요한 데이터를 불러 온다.


```python
!kaggle competitions download -c titanic # download -c, 다운 받을 대회명 진행중인 대회 동의 안되 있으면
# Warning: Looks like you're using an outdated API Version, please consider updating 같은 문구 나옴, 대회 동의 하면 다운가능
```

    Warning: Looks like you're using an outdated API Version, please consider updating (server 1.5.9 / client 1.5.4)
    Downloading test.csv to /content/drive/My Drive/Colab Notebooks/learn_kaggle
      0% 0.00/28.0k [00:00<?, ?B/s]
    100% 28.0k/28.0k [00:00<00:00, 3.73MB/s]
    Downloading train.csv to /content/drive/My Drive/Colab Notebooks/learn_kaggle
      0% 0.00/59.8k [00:00<?, ?B/s]
    100% 59.8k/59.8k [00:00<00:00, 8.37MB/s]
    Downloading gender_submission.csv to /content/drive/My Drive/Colab Notebooks/learn_kaggle
      0% 0.00/3.18k [00:00<?, ?B/s]
    100% 3.18k/3.18k [00:00<00:00, 438kB/s]
    

kaggle에서 불러온 파일이 제대로 들어와 있는지 확인한다.


```python
!ls # 데이터 확인
```

    gender_submission.csv  sample_data  test.csv  train.csv
    

# 구글 드라이브 저장

## 마운트 설정

코드를 실행하여 구글 드라이브에 마운트를 설정한다. * 마운트: 저장 장치에 접근할 수 있는 경로를 디렉터리 구조에 편입시키는 작업

아래의 코드를 진행한뒤 본인계정의 연동을 진행한다.


```python
from google.colab import drive # 패키지 불러오기 

ROOT = "/content/drive"     # 드라이브 기본 경로
print(ROOT)                 # print content of ROOT (Optional)
drive.mount(ROOT)           # 드라이브 기본 경로 Mount
```

    /content/drive
    Mounted at /content/drive
    

연동 후 colab을 실행 하면 Colab Notebooks 문서가 생성된다.생성이 된것을 확인하면 Colab Notebooks 문서 안에 data를 저장할 수 있는 새로운 문서를 만든다.<br>
문서를 만들시 뛰어쓰기, 한글은 들어가지 않도록 유의 하자.<br>

## 데이터 저장

문서을 생성 했다면 생성한 문서로 경로를 지정해 주고 실행하면 데이터가 업로드 된다.


```python
from os.path import join  

MY_GOOGLE_DRIVE_PATH = 'My Drive/Colab Notebooks/learn_kaggle'
PROJECT_PATH = join(ROOT, MY_GOOGLE_DRIVE_PATH)
print(PROJECT_PATH)
```

    /content/drive/My Drive/Colab Notebooks/learn_kaggle
    

아래의 코드로 저장된 위치가 문제 없는지 확인해 본다.


```python
%cd "{PROJECT_PATH}"
```

    /content/drive/My Drive/Colab Notebooks/learn_kaggle
    
