# 3DCNN-MQA

## Requirement
- python==3.6
- Chainer==5.2.0
- Prody==1.10.8
- Biopython==1.72
- Emboss[1]
- Scwrl4[2]
## Preparation

- Download pre-trained model from [here](http://www.cb.cs.titech.ac.jp/~sato/bmc2018/pretrained_model.npz).
- export PATH to emboss package to use needle
## Usage
```bash
cd your_download_directory/source

# Side chain optimization before prediction
Scwrl -i ../sample/T0759_sample.pdb -o ../sample/T0759_sample.pdb


# Predict Model Quality Score from PDB (using GPU)
python predict_from_pdb.py -i ../sample/T0759_sample.pdb -m pre-trained_model_path -g 0

# Predict Model Quality Score from PDB (using CPU)
python predict_from_pdb.py -i ../sample/T0759_sample.pdb -m pretrained_model_path

# If you have reference fasta file
python predict_from_pdb.py -i ../sample/T0759_sample.pdb -r ../sample/T0759.fasta -m pre-trained_model_path -g 0

```
## Sample Output
```text
Needleman-Wunsch global alignment of two sequences
Input Data Path : /gs/hs0/tga-ishidalab/sato/dataset/test_set_not_H/pdb_style/casp11/stage_1/T0759/T0759TS022_2.pdb
Model Quality Score : 0.2598034739494324
Resid	Resname	Score
13	VAL	0.18779
14	ILE	0.37449
15	HIS	0.18374
16	PRO	0.41228
17	ASP	0.29165
...
```


## Reference
[1] : EMBOSS: The European Molecular Biology Open Software Suite (2000) 
Rice,P. Longden,I. and Bleasby,A. 
Trends in Genetics 16, (6) pp276--277

[2] : G. G. Krivov, M. V. Shapovalov, and R. L. Dunbrack, Jr. Improved prediction of protein side-chain conformations with SCWRL4. Proteins (2009).


