## image registration/normalization
- scalp stripping
```
bet 3dt2-s275.nii.gz 3dt2-s275-bet.nii.gz -v
```
- registration: native structural (T2) to template (T2)
```
flirt -ref ../atlas/BCP-atlas-for_release-Ver2.0.0/00Month/BCP-00M-T2.nii.gz -in 3dt2-s275-bet.nii.gz -out highres2standard -omat highres2standard.mat -searchrx -50 50 -searchry -50 50 -searchrz -10 10 -v
```
![T2 atlas](https://github.com/fahsuanlin/study_preterm/blob/main/images/t2_template.png?raw=true)
