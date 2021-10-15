# 칠성사이다
![image](https://user-images.githubusercontent.com/20790778/137433985-622be56d-82eb-4dd7-bbec-c7079b0bf059.png)

## Requirements
- python, numpy, pandas
- pytorch
- mmdetection
- torchvision
- albumentations
- seaborn
- https://github.com/open-mmlab/mmdetection
- https://github.com/shinya7y/UniverseNet
- https://github.com/ZFTurbo/Weighted-Boxes-Fusion

## contents
```
object-detection-level2-cv-06(*detection)/
├── EDA/ # custom EDA files
├── dataset/
│   ├─ candidate/ # custom dataset candidate
│   ├─ sample.json # just sample
│   ├─ test.json # orginal test.json, full data
│   ├─ train.json # orginal train.json, full data
│   ├─ team_train.json # 팀에서 자체적으로 설정한 train set (train.json의 subset)
│   └─team_valid.json # 팀에서 자체적으로 설정한 valid set (train.json의 subset)
├── mmconfig/ # mmdetection용 config 모음
│   ├─ datasets/ # dataset configs
│   ├─ models/ # model configs
│   │  └─ pretrained/ # pretrained save pth path
│   ├─ schedules/ # schedule configs
│   ├─ runtime/ # runtime configs
│   ├─ sample/ # old style configs, current not used
│   ├─ listup/ # test config에서 선택되어 분류된 config들
│   └─ test/ # [datasets, models, schedules, runtime] config 들을 통합한 main config
├── utils/ # 부가적으로 필요한 util들  
│   ├─ ensemble_models/ 앙상블 할 출력물 경로(해당 폴더내에 csv파일을 대상으로 선택한다)
│   │  └─ output/ 앙상블 결과 파일이 저장되는 경로
│   ├─ EDA.ipynb # main EDA
│   ├─ anno_converter.ipynb # coco dataset json 파일을 조건에따라 샘플링하여 파일로 저장해주는 converter
│   ├─ csv2json.py # 제출용 submission csv 파일을 다시 coco 형태의 json 파일로 변경해주는 파일 (presudo labeling 등에 사용)
│   ├─ final_ensemble.py # ensemble_models/안의 csv 파일을 여러 옵션으로 앙상블하여 output/에 저장
│   ├─ inference.py # mmdetection 에서 생성된 output 모델을 inference 하여 결과 csv 파일 생성
│   ├─ merge_json.py # 여러 coco 형태의 json 파일 하나의 파일로 병합 (단, mmdetection 에서는 dataset을 list 형태로 여러개 넣어주는 방법도 가능하다)
│   ├─ mosaic_create.py # dataset의 image와 annotation을 모자이크 기법을 활용해 새로운 파일로 저장
│   ├─ submission_viewer.ipynb # 제출용 submission csv 파일을 읽어 시각적으로 확인할 수 있게 해주는 viewer
│   └─ viewer.ipynb # 조건에 따라 이미지 단위, 오브젝트 단위로 이미지를 볼 수있는 viewer
├── work_dirs/ # 작업 결과가 저장되는 경로  
│   └─ *listup/ # 작업 결과들 중에 공유가 필요하다고 선택된 출력파일을 폴더 단위로 업로드
└── mmdetection/ # import mmdetection library in this path
```
- mmdetection의 load_from 이 절대경로밖에 지원하지 않아 object-detection-level2-cv-06이 detection이 되어야합니다. (`/opt/ml/detection/`)
- `work_dirs/listup/` 내의 각 폴더는 [\*.log, \*.py, \*.pth] 폴더를 포함한다.
  - \*.log : 최종 출력 로그
  - \*.py : 최종 config 파일
  - \*.pth : 최종 제출에 사용된 checkpoint
