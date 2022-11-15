# Urban Sound Monitoring (USM) Dataset - A Dataset for Polyphonic Sound Event Tagging in Urban Sound Monitoring Scenarios

## Reference

- Jakob Abeßer: *Classifying Sounds in Polyphonic Urban Sound Scenes*, Proceedings of the 152nd AES Convention (2022), [Paper pre-print (PDF)](./paper/Abesser_2022_UrbanSoundsPreprint_AES.pdf)

## Demo

You can find a 10 minute long demo video with mel spectrogram visualizations of both mixtures and the corresponding stems at [https://www.youtube.com/watch?v=pVKB2xeBOJA](https://www.youtube.com/watch?v=pVKB2xeBOJA).
 
## Description 

This dataset includes **24,000** **5-seconds-long** polyphonic stereo soundscapes composed of sounds taken from the FSD50k dataset:

- Eduardo Fonseca, Xavier Favory, Jordi Pons, Frederic Font, Xavier Serra. [FSD50K: an Open Dataset of Human-Labeled Sound Events](https://arxiv.org/abs/2010.00475), arXiv:2010.00475, 2020, :floppy_disk: [Dataset description & download](https://zenodo.org/record/4060432)

FSD50k samples were selected to allow for commercial usage (see [licence file](LICENCE.md))!

The process of mixing the polyphonic soundscapes is detailed in the AES paper (see "Reference").

## USM Dataset Download

:floppy_disk: The USM dataset can be downloaded from [https://zenodo.org/record/6413788](https://zenodo.org/record/6413788).

## Urban Sound Application Scenarios

A subset of the original FSD50k sound classes are mapped to 26 new sound classes potentially relevant in urban sound monitoring scenarios such as
  - :car: :bus: :helicopter: traffic monitoring
  - :construction: construction site monitoring
  - :bomb: :rotating_light: :scream:recognition of rare security-relevant events
  - :bird: :dog: bioacoustic monitoring
  - :umbrella: :cloud: :zap: weather monitoring

## Sound Classes

The USM dataset includes 26 sound classes

- airplane, alarm, birds, bus, car, cheering, church bell, dogs, drilling, glass break, gunshot, hammer, helicopter, jackhammer, lawn mower, motorcycle, music, rain, sawing, scream, siren, speech, thunderstorm, train, truck, wind

## Dataset Split

The USM-SED dataset contains 22,000 soundscapes in its **development set** (composed of sounds of the FSD50k development 
set) and 2,000 soundscapes 
in its **evaluation set** (composed of sounds of the FSD50k evaluation set).

The development set is further divided into a **training set** (20,000 soundscapes) and a **validation set** (2,000 soundscapes).


| USM dataset | FSD50k dataset (source) | Soundscapes  |
| :-------------   | :----------:   | -----------: |
|  Training        | Development    | 20,000       |
|  Validation      | Development    |  2,000       |
|  Evaluation      | Evaluation     |  2,000       |


## Dataset structure

- the dataset folder includes 3 folders
  - `train` (training set)
  - `val` (validation set)
  - `eval` (evaluation set)
- For each soundscape, you can find
  - one (stereo) audio file: e.g. `3_mix.wav`
  - multiple (mono) audio files with the isolated stems, e.g. `3_mix_stem_0.wav`, `3_mix_stem_1.wav`, etc. 
  - one binary numpy file with the multi-label targets (26 classes), e.g. `3_mix_targets.npy`
  - multiple binary numpy files with the single-label targets for the stems (26 classes), e.g. `3_stem_0_target.npy`
  
## Metadata

- in the `metadata` folder in this repository you can find
  - `class_labels.csv` - all sound classes
  - `usm_{train/val/eval}.csv` - CSV files with details about sample composition of all polyphonic soundscapes in the training (train), validation (val), and evaluation (eval) datasets, the following columns are used in the CSV file:
    - _ID_
    - _class_usm_ (USM sound class)
    - _class_fsd_ (original sample sound label in FSD50k dataset)
    - _file_ (original filename in FSD50k dataset)
    - _licence_ (licence, the original sample was published under)
    - _dur_sec_ (original sample duration in seconds)
    - _part_ (FSD50k subset (dev / eval) the sample came from)
    - _init_silence_sec_ (initial silence added in the processed sample)
    - _on_sec_ (sample onset in the original sample)
    - _off_sec_ (sample offset in the original sample)
    - _is_foreground_ (bool to indicate whether sound is foreground or background sound, see paper for details)
    - _mix_coeff_db_ (mixing coefficient in dB)
    - _stereo_coeff_ (stereo placement coefficient)
    - _usm_id_ (soundscape ID within the USM dataset, each sample is mixed to)  
    
   
## Acknowledgement

This work has been supported by the German Research Foundation (AB 675/2-2). 
