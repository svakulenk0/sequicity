# Sequicity

Source code for the ACL 2018 paper entitled "Sequicity: Simplifying Task-oriented Dialogue Systems with Single Sequence-to-Sequence 
Architectures" by Wenqiang Lei et al.

```
@inproceedings{lei2018sequicity,
  title={Sequicity: Simplifying Task-oriented Dialogue Systems with Single Sequence-to-Sequence Architectures},
  author={Lei, Wenqiang and Jin, Xisen and Ren, Zhaochun and He, Xiangnan and Kan, Min-Yen and Yin, Dawei},
  year={2018},
  organization={ACL}
}
```


## Training with default parameters

```
python3 model.py -mode train -model tsdf-OD
```

(optional: configuring hyperparameters with cmdline)

```
python model.py -mode train -model [tsdf-camrest|tsdf-kvret] -config lr=0.003 batch_size=32
```

## Testing

```
python3 model.py -mode test -model tsdf-OD
```

## Reinforcement fine-tuning

```
python3 model.py -mode rl -model tsdf-camrest
```

## Inference

```
python3 model.py -mode iteract -model tsdf-OD
```

## Before running
1. Install required python packages. We used pytorch 0.3.0 and python 3.6 under Linux operating system. 
```
pip install -r requirements.txt
```
2. Make directories under PROJECT_ROOT.
```
mkdir vocab
mkdir log
mkdir results
mkdir models
mkdir sheets
```

3. Download pretrained word vectors:

e.g. English Glove 6B tokens, 400K vocab, uncased, 50 dimensions
```
mkdir data/glove
cd data/glove
wget http://nlp.stanford.edu/data/glove.6B.zip
unzip glove.6B.zip
```

or German [fasttext](https://github.com/facebookresearch/fastText/blob/master/pretrained-vectors.md)

```
mkdir data/fasttext
cd data/fasttext
wget https://s3-us-west-1.amazonaws.com/fasttext-vectors/wiki.de.zip
unzip wiki.de.zip
```

4. Download NLTK stopwords

In Python console:
```
>>> import nltk
>>> nltk.download()
Downloader> d
Identifier> stopwords
```