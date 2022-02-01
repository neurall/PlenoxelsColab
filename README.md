# Plenoxels: Colab version

https://colab.research.google.com/drive/1SODy_HiP_kkjL5E4IiBM1XZsD1HofElZ

This is an attempt to make running in colab cloud possible for the wonderfull breakthrough that is Plenoxels made by fantastic team of incredibly talented

# Plenoxels Authors: (Alex Yu * Sara Fridovich-Keil * Matthew Tancik Qinhong Chen Benjamin Recht Angjoo Kanazawa UC Berkeley * Equal contribution)
Github: https://github.com/sxyu/svox2
Website and video: https://alexyu.net/plenoxels
arXiv: https://arxiv.org/abs/2112.05131

I was just thinking UE5 nanite conversion anyone ? ;D I guess marching cubes ?
Just thing about the possibilities from bunch of mobile photos straight to realtime VR experience?

This first version seems to work at least on Colab Pro providing 16g gpu and with high mem option enabled(32g ram) to fit and train M60 dataset (Colab Pro is 10$ a month which is price of 1 hamburger)

This colab will currently sadly not yet work on free colab (but deffinitely can soon?) instance due to size of datasets. And niether will it probably reasonably well work (if you reduce res it will fit in gpu mem but output typically will be unusable) on any gpu commonly at your pc like 10g 3080 or 11g 1080

Free colab has just 12g ram 11g (P8) gpu or 15g (t4?) gpu and this svox2 variant needs at least 27g ram and at least 16g gpu (p100?) for training datasets of similar size as cool M60 Tank dataset from my observations so far
Hmm when you think about it These Larger datasets should be splitable to smaller ones fitting 4-24g gpus by estimated camera locations from bundle adjustment colmap files that datasets already have?

Multi gpu (or multipass for free colab?) can work in theory like this

Say you have 2 * 11g gpus. Split dataset photos to 2 * 2 chunks ABCD by estimated cam positions that datasets already have

Then train on as many gpus in paralell as you want

pass1 train individual scene fragments
gpu1:AB gpu2:CD

pass2 to solve underrepresented voxels from border regions of chunks to allow good merge of seams
gpu1:BC gpu2:DA

merge pass1 and pass2

Datasets: NeRF-synthetic and front facing llff: https://drive.google.com/drive/folders/128yBriW1IG_3NJ5Rp7APSTZsJqdJdfc1
Processed Tanks and temples dataset (with background): https://drive.google.com/file/d/1PD4oTP4F8jTtpjd_AQjCsL4h8iYFCyvO
Real Lego capture: https://drive.google.com/file/d/1PG-KllCv4vSRPO7n5lpBjyTjlUyT8Nag
Pretrained checkpoints (good if you cant train?): https://drive.google.com/drive/folders/1SOEJDw8mot7kf5viUK9XryOAmZGe_vvE
