# Learning Individual Styles of Gestures - Data page
#### [Shiry Ginosar](http://people.eecs.berkeley.edu/~shiry) *, [Amir Bar](http://amirbar.github.io) *, Gefen Kohavi, [Caroline Chan](https://www.csail.mit.edu/person/caroline-chan), [Andrew Owens](http://andrewowens.com/), [Jitendra Malik](https://people.eecs.berkeley.edu/~malik/)![alt text](../data/teaser_gan_oliver_041.png "")
##### Back to [main project page](https://people.eecs.berkeley.edu/~shiry/projects/speech2gesture/index.html)


## Table of contents:
1. [Download specific speaker data](#Download-specific-speaker-data)
2. [Crop intervals containing frontal speaker](#Crop-intervals-containing-frontal-speaker)
3. [Reference](#reference)

## Download specific speaker data
### Frames.csv File

1. Create a base dataset folder named (e.g Gestures)
2. Download the file `frames_df.csv.tgz` from [here](https://drive.google.com/drive/folders/1qvvnfGwas8DUBrwD4DoBnvj8anjSLldZ). extract in the root path of base folder. This file contains a listing and metadata of all included files. 

After this step, this should be the contents of your base dataset folder:
```
Gestures
└── frames.csv
```


`frames.csv` is a csv file in which every row represents a single frame in the data.  
![alt text](../data/frames.png "")

#### Columns documentation:
```
frame_fn - name of the frame file
pose_dt - frame time in the video
pose_fn - serialized file containing poses
speaker - name of a speaker in the dataset
video_fn - name of the video file
interval_id - unique id of the interval in which the frame appears. interval in this scope is a part of video in which the speaker appears in a clean, frontal way.
dataset - train/dev/test
video_link - video youtube link   
```

### Download speaker data

3. Download a single or multiple speakers keypoints & frames tar file [here](https://drive.google.com/drive/folders/1qvvnfGwas8DUBrwD4DoBnvj8anjSLldZ). Extract this file directly in the base folder. 
After this step, your dataset folder should be in the following structure:
```
Gestures
├── frames.csv
├── almaram
│   ├── frames
│   ├── keypoints_all
│   └── keypoints_simple
...
└── shelly
    ├── frames
    ├── keypoints_all
    └── keypoints_simple
```
 
4. Download the speaker videos from youtube. Use the script attached:
`python -m data.download.download_youtube --base_path </path/to/dataset base folder> --speaker <speaker_name>`

Speaker names include: 
oliver, jon, conan, rock, chemistry, ellen, almaram, angelica, seth, shelly


After this step, your dataset folder should be of the following structure:
```
Gestures
├── frames.csv
├── almaram
    ├── frames
    ├── videos
    ├── keypoints_all
    ├── keypoints_simple
    └── videos
...
└── shelly
    ├── frames
    ├── videos
    ├── keypoints_all
    ├── keypoints_simple
    └── videos
```

## Crop intervals containing frontal speaker

If you just want to use intervals containing frontal view of the speakers for any purpose, follow these instructions

1. Follow "Download specific speaker data" section
2. Download `intervals_df.csv` and `crop_intervals.csv` from [here](https://drive.google.com/drive/folders/1qvvnfGwas8DUBrwD4DoBnvj8anjSLldZ) and position it in base path.3
3. Run: 

```python crop_intervals --base_path </path/to/base folder> --speaker <optional, speaker_name> --output_path <output path to save intervals>```

---


Notes:
Currently, this script will only download youtube videos so all non-youtube links will be skipped. Broken video links will be skipped.

### Reference
If you found this code useful, please cite the following paper:


```
@InProceedings{ginosar2019gestures,
  author={S. Ginosar and A. Bar and G. Kohavi and C. Chan and A. Owens and J. Malik},
  title = {Learning Individual Styles of Conversational Gesture},
  booktitle = {Computer Vision and Pattern Recognition (CVPR)}
  publisher = {IEEE},
  year={2019},
  month=jun
}
```
