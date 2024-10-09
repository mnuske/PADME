# PADME

Using PriMAT and OpenMonkeyStudio as baseline models:

> [**PriMAT: A robust multi-animal tracking model for primates in the wild**](https://www.biorxiv.org/content/10.1101/2024.08.21.607881v1)\
>  Richard Vogg, Matthias Nuske, Marissa A. Weis, Timo Lüddecke, Elif Karakoç, Zurna Ahmed, Sofia M. Pereira, Suchinda Malaivijitnond, Suthirote Meesawat, Florentin Wörgötter, Peter M. Kappeler, Alexander Gail, Julia Ostner, Oliver Schülke, Claudia Fichtel, Alexander S. Ecker

> [**Automated markerless pose estimation in freely moving macaques with OpenMonkeyStudio**](https://www.nature.com/articles/s41467-020-18441-5)\
> Praneet C. Bala, Benjamin R. Eisenreich, Seng Bum Michael Yoo, Benjamin Y. Hayden, Hyun Soo Park & Jan Zimmermann

## Setup

- Clone this repo, and we'll call the directory that you cloned as ${PADME_ROOT}
- Install dependencies. We use python 3.8 and pytorch >= 1.7.0 (All needed packages are included in the environment.yaml file).

```
conda env create -f environment.yaml
conda activate padme
cd ${PADME_ROOT}
```
<!--- can be added through conda-forge::ffmpeg
- In order to run the code on videos, [ffmpeg](https://www.ffmpeg.org/) is needed.

```
sudo apt install ffmpeg
```
-->


## Data preparation
<!--
In general we would like to have the data for training in one folder. This folder has two subfolders, images and labels_with_ids.

```
dataset_folder
   |——————images
   |        └——————IMG0001.jpg
   |        └——————IMG0002.jpg
   |        ...
   └——————labels_with_ids
```         
-->

## Pretrained models and baseline model

- **Pretrained models**


- **Baseline model**
<!--
The baseline FairMOT model (DLA-34 backbone) is pretrained on the CrowdHuman for 60 epochs with the self-supervised learning approach and then trained on the MIX dataset for 30 epochs. The models can be downloaded here:
crowdhuman_dla34.pth [[Google]](https://drive.google.com/file/d/1SFOhg_vos_xSYHLMTDGFVZBYjo8cr2fG/view?usp=sharing) [[Baidu, code:ggzx]](https://pan.baidu.com/s/1JZMCVDyQnQCa5veO73YaMw) [[Onedrive]](https://microsoftapc-my.sharepoint.com/:u:/g/personal/v-yifzha_microsoft_com/EUsj0hkTNuhKkj9bo9kE7ZsBpmHvqDz6DylPQPhm94Y08w?e=3OF4XN).
-->

After downloading, you should put the models in the following structure:

```
${PADME_ROOT}
   └——————models
           └——————fairmot_dla34.pth
           └——————ctdet_coco_dla_2x.pth
```

## Training

- Download the training data
- Change the dataset root directory 'root' in src/lib/cfg/data.json and 'data_dir' in src/lib/opts.py
- Pretrain on CrowdHuman and train on MIX:


## Videos

You can input a raw video and get the demo video by running src/demo.py and get the mp4 format of the demo video:
<!--
```
cd src
python demo.py mot --load_model ../models/fairmot_dla34.pth --conf_thres 0.4
```

You can change --input-video and --output-root to get the demos of your own videos.
--conf_thres can be set from 0.3 to 0.7 depending on your own videos.
-->

## Train on custom dataset

You can train PADME on a custom dataset by following the steps below:
<!--
1. Generate one txt label file for one image. Each line of the txt label file represents one object. The format of the line is: "class id x_center/img_width y_center/img_height w/img_width h/img_height". You can modify src/gen_labels_16.py to generate label files for your custom dataset.
2. Generate files containing image paths. The example files are in src/data/. Some similar code can be found in src/gen_labels_crowd.py
3. Create a json file for your custom dataset in src/lib/cfg/. You need to specify the "root" and "train" keys in the json file. You can find some examples in src/lib/cfg/.
4. Add --data_cfg '../src/lib/cfg/your_dataset.json' when training.
-->

## Acknowledgement

This project builds on ---

* We will finetune the model on MacaquePose and OpenMonkeyStudio data.


## Citation of PriMAT

```
@article {Vogg2024.08.21.607881,
	author = {Vogg, Richard and Nuske, Matthias and Weis, Marissa A. and L{\"u}ddecke, Timo and Karako{\c c}, Elif and Ahmed, Zurna and Pereira, Sofia M. and Malaivijitnond, Suchinda and Meesawat, Suthirote and W{\"o}rg{\"o}tter, Florentin and Kappeler, Peter M. and Gail, Alexander and Ostner, Julia and Sch{\"u}lke, Oliver and Fichtel, Claudia and Ecker, Alexander S.},
	title = {PriMAT: A robust multi-animal tracking model for primates in the wild},
	doi = {10.1101/2024.08.21.607881},
	URL = {https://www.biorxiv.org/content/early/2024/08/21/2024.08.21.607881},
	journal = {bioRxiv}
}
```
