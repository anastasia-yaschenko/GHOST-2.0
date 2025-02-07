# GHOST-2.0

## TODO
- [ ] Blender code
- [ ] Blender checkpoint
- [ ] Complete instruction (project page)
- [ ] Add blender to inference script ```inference.py```
- [ ] Add segmentation model to preprocessing script ```preprocess_image.py```

## Installation
Clone repo with option ```--recurse-submodules```
Install conda environment:
```
conda create -n ghost python=3.10

pip install face-alignment
pip install facenet_pytorch

conda config --add channels conda-forge
conda config --set channel_priority strict
pip install -U 'git+https://github.com/facebookresearch/fvcore'
conda install pytorch3d -c pytorch3d-nightly

pip install -r requirements.txt
python -m pip uninstall numpy
python -m pip install numpy==1.23.1
```
Set up the following repositories in the ```repo``` folder:
[DECA](https://github.com/yfeng95/DECA)
[EMOCA](https://github.com/radekd91/emoca)
[BlazeFace](https://github.com/hollance/BlazeFace-PyTorch)
[stylematte](https://github.com/chroneus/stylematte)

Download the models from releases. Place them into the following folders
```
- aligner_checkpoints
    - aligner_1020_gaze_final.ckpt

- src
    - losses
        - gaze_models
 
- weights
    - backbone50_1.pth
    - vgg19-d01eb7cb.pth
```

## Inference
For inference run
```
python inference.py --source ./examples/images/hab.jpg --target ./examples/images/elon.jpg --save_path result.png
```

## Training
1. Download VoxCeleb2. We expect the following structure of data directory and assume images are stored in BGR format:
```
- train
    - person_id
        - video_folder
            -h5 video files
-test
```
2. Preprocess data according to the example in file ```preprocess_image.py```
3. To train Aligner, run ```python train_aligner.py```

## Citation

## Acknowledgements
This work utilizes code from the follwing repositories:
[Neural Head Reenactment with Latent Pose Descriptors](https://github.com/shrubb/latent-pose-reenactment)
[EMOPortraits: Emotion-enhanced Multimodal One-shot Head Avatars](https://github.com/neeek2303/EMOPortraits)