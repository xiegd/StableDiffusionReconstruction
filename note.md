# Note

## 文件说明

StableDiffusionReconstruction 这个方法

MRI Preprocessing

``` bash
cd codes/utils/
python make_subjmri.py --subject subj01
```

Reconstruction based on CVPR method

```bash
cd codes/utils/
python img2feat_sd1.py  --imgidx 0 73000 --gpu 0
python make_subjstim.py --featname init_latent --use_stim each --subject subj01
python make_subjstim.py --featname init_latent --use_stim ave --subject subj01
python make_subjstim.py --featname c --use_stim each --subject subj01
python make_subjstim.py --featname c --use_stim ave --subject subj01
python ridge.py --target c --roi ventral --subject subj01
python ridge.py --target init_latent --roi early --subject subj01

cd codes/diffusion_sd1/
python diffusion_decoding.py --imgidx 0 10 --gpu 1 --subject subj01 --method cvpr
```
