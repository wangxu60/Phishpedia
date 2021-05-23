# Phishpedia

- This is the official implementation of "Phishpedia: A Hybrid Deep Learning Based Approach to Visually Identify Phishing Webpages" USENIX'21 [[paper](https://www.usenix.org/conference/usenixsecurity21/presentation/lin)]
    
### [Framework]
    
<img src="big_pic/pic.png" style="width:2000px;height:350px"/>

```Input```: A URL and its screenshot ```Output```: Phish/Benign, Phishing target
- Step 1: Enter <b>Deep Object Detection Model</b>, get predicted elements

- Step 2: Enter <b>Deep Siamese Model</b>
    - If Siamese report no target, ```Return  Benign, None```
    - Else Siamese report a target, ```Return Phish, Phishing target``` 


### [Instructions]
1. Download all the model files:
- First 
```
cd src/phishpedia
```
``` 
wget https://drive.google.com/file/d/1H0Q_DbdKPLFcZee8I14K62qV7TTy7xvS/view?usp=sharing
```
``` 
wget https://drive.google.com/file/d/1_C8NSQYWkpW_-tW8WzFaBr8vDeBAWQ87/view?usp=sharing
```
``` 
wget https://drive.google.com/file/d/1qSdkSSoCYUkZMKs44Rup_1DPBxHnEKl1/view?usp=sharing
```

- Then 
```
cd src/detectron2_pedia/output/rcnn_2
```
```
wget https://drive.google.com/file/d/1tE2Mu5WC8uqCxei3XqAd7AWaP5JTmVWH/view?usp=sharing
```

- Afterwards 
```
cd src/siamese_retrain
```
```
wget https://drive.google.com/file/d/1cuGAGe-HubaQWU8Gwn0evKSOake6hCTZ/view?usp=sharing
```
```
wget https://drive.google.com/file/d/1GirhWiOVQpJWafhHA93elMfsUrxJzr9f/view?usp=sharing
```
```
wget https://drive.google.com/file/d/12GjdcYeSBbPji8pCq5KrFhWmqUC451Pc/view?usp=sharing
```
2. Download all data files
- Download phish30k, benign30k dataset:
```
cd datasets
wget https://drive.google.com/file/d/12ypEMPRQ43zGRqHGut0Esq2z5en0DH4g/view?usp=sharing
wget https://drive.google.com/file/d/1yORUeSrF5vGcgxYrsCoqXcpOUHt-iHq_/view?usp=sharing
```
- Download labelled benign30k dataset (optional, if you want to train Faster-RCNN yourself):
```
cd datasets
wget 
```
3. Run experiment 
- For phish discovery experiment:
```
python phishpedia_main.py --folder [data folder you want to test] --results [xxx.txt]
```
- For general experiment: 
please run evaluation scripts
```
python -m src.pipeline_eval --data-dir datasets/phish_sample_30k --mode phish --write-txt output_phish.txt --ts [threshold for siamese]
```
```
python -m src.pipeline_eval --data-dir datasets/benign_sample_30k --mode benign --write-txt output_benign.txt --ts [threshold for siamese]
```
- For adversarial attack on Siamese, download all files [[here]()] and put them under **datasets/**:


### [Training the model]
1. If you want to train object detection faster-rcnn model, 
- First dowonload training data
```
cd datasets
wget https://drive.google.com/file/d/1L3KSWEXcnWzYdJ4hPrNEUvC8jaaNOiBa/view?usp=sharing
unzip data.zip -d . 
```


### [Project structure]
- src
    - phishpedia: training script for siamese
    - element_detector: training script for element detector
    - util: other scripts (chromedriver utilities)
    - element_detector.py: main script for element detector
    - siamese.py: main script for siamese

        