## image registration/normalization
- scalp stripping
```
bet 3dt2-s275.nii.gz 3dt2-s275-bet.nii.gz -v
```
- registration: native structural (T2) to template (T2)
```
flirt -ref ../atlas/BCP-atlas-for_release-Ver2.0.0/00Month/BCP-00M-T2.nii.gz -in 3dt2-s275-bet.nii.gz -out highres2standard -omat highres2standard.mat -searchrx -50 50 -searchry -50 50 -searchrz -10 10 -v
```

T2-weighted atlas ![T2 atlas](https://github.com/fahsuanlin/study_preterm/blob/main/images/t2_template.png?raw=true)

Native T2-weighted image ![T2 native](https://github.com/fahsuanlin/study_preterm/blob/main/images/t2_native.png?raw=true)

Native T2-weighted image after skull stripping ![T2 native bet](https://github.com/fahsuanlin/study_preterm/blob/main/images/t2_native_bet.png?raw=true)

Native T2-weighted image normalized to atlas ![T2 native bet](https://github.com/fahsuanlin/study_preterm/blob/main/images/t2_bet_native2template.png?raw=true)

