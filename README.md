# segmentation-transfer

To launch any `make` with reference to local directories (`./data` and `./models`), pass the anything to the variable `local` other than `false`. For example,

```
make all local=1
make all local=true
```
The above will run with the local subdirectories as reference.

The default is to point to the Mila file system for data and models. See [the makefile](makefile) for more info.


## Tiny dataset

The code can run on tiny versions of the datasets using the following command.

```
make tiny-segnet
```

 See [the makefile](makefile) for more info. Please be aware the tiny versions of the dataset can be made using [this file](src/data/tiny_dataset.py).

---

# Environment

Dependencies are listed in [`environment.yml`](environment.yml). To create the conda environment, use the following command.

```
conda env create -f environment.yml
```

# Data

Data files `classes.hdf5`, `sim.hdf5` and `real.hdf5` must be placed in `hdf5`

## Real Duckiebot images

The database of logs can be found [here](http://ipfs.duckietown.org:8080/ipfs/QmUbtwQ3QZKmmz5qTjKM3z8LJjsrKBWLUnnzoE5L4M7y7J/logs/gallery.html). Files can be directly downloaded from [here](https://gateway.ipfs.io/ipfs/QmUbtwQ3QZKmmz5qTjKM3z8LJjsrKBWLUnnzoE5L4M7y7J/logs/) using the following command.

```
make data/videos/download.info
```

A list of videos used is listed in the file [`data/videos/list_of_videos.txt`](data/videos/list_of_videos.txt).

#### Extracting frames

Frames were extracted from the raw videos from the logs and downsampled from 640x480 to 160x120. Extracting every 10 frames of the downloaded videos provided a dataset of 11419 images.

To extract the frames from the set of downloaded videos, simply use the following command.

```
make data/videos/real.hdf5
```
