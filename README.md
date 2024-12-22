## image registration/normalization
1. register and normalize between atlas and individual's structural MRI
   
- scalp stripping
```
bet 3dt2-s275.nii.gz 3dt2-s275-bet.nii.gz -v
```
- registration: native structural (T2) to template (T2)
```
flirt -ref ../atlas/BCP-atlas-for_release-Ver2.0.0/00Month/BCP-00M-T2.nii.gz -in 3dt2-s275-bet.nii.gz -out highres2standard -omat highres2standard.mat -searchrx -50 50 -searchry -50 50 -searchrz -10 10 -v
```
Atlas          |  Native T2 |  Native T2 after skill stripping | Native T2 normalized
:-------------:|:----------:|:--------------------------------:|:-------------------------:
![](https://github.com/fahsuanlin/study_preterm/blob/main/images/t2_template.png?raw=true)  | ![](https://github.com/fahsuanlin/study_preterm/blob/main/images/t2_native.png?raw=true)| ![](https://github.com/fahsuanlin/study_preterm/blob/main/images/t2_bet_native.png?raw=true) | ![](https://github.com/fahsuanlin/study_preterm/blob/main/images/t2_bet_native2template.png?raw=true)

2. register and normalize between individual's structural MRI and functional MRI

  **A smaller range of rotation is allowed.
  
  ```
  	flirt -ref 3dt2-s285 -in fmri_s285 -out whole_func2highres -omat whole_func2highres.mat -searchrx -3 3 -searchry -3 3 -searchrz -3 3 -v
  ```

3. combine two registration matrices (functional to structural; structural to atlas) to register and normalize fMRI:

- combine two registration matrices
  ```
  convert_xfm -concat highres2standard.mat -omat func2standard.mat whole_func2highres.mat
  ```
- apply the combined registration matrix to fMRI:
 ```
flirt -ref ../atlas/BCP-atlas-for_release-Ver2.0.0/00Month/BCP-00M-T2.nii.gz -in fmri_s285 -applyxfm -init func2standard.mat -out fmri2standard
```
