# earth

Landscape manipulation of Neural 3D Graphics

# `Instant-ngp`

## Compilation (Windows & Linux)

Use instructions from [https://github.com/bycloudai/instant-ngp-Windows](https://github.com/bycloudai/instant-ngp-Windows)

Begin by cloning this repository and all its submodules using the following command:

```sh
$ git clone --recursive https://github.com/nvlabs/instant-ngp
$ cd instant-ngp
```

- Create `conda` env and install requirements
- Be sure to install ngp (`pip install pyexr`)

  Then, use CMake to build the project: (on Windows, this must be in a [developer command prompt](https://docs.microsoft.com/en-us/cpp/build/building-on-the-command-line?view=msvc-160#developer_command_prompt))

```sh
instant-ngp$ cmake . -B build
instant-ngp$ cmake --build build --config RelWithDebInfo -j
```

## Run

```
# DATASET LOCATION (i.e.)
	instant-ngp\data\nerf\house

# RUN COLMAP
python scripts\colmap2nerf.py --colmap_matcher exhaustive --run_colmap --aabb_scale 16 --images data\nerf\house

# RUN
.\build\testbed --scene .\transforms.json


# RENDER mp4
python scripts/run.py --mode nerf --scene data/nerf/house --load_snapshot transforms_base.msgpack --video_camera_path transforms_base_cam.json --video_n_seconds 5 --video_fps 60 --width 960 --height 540

python scripts/render.py --scene data/nerf/house --n_seconds 5 --fps 30 --render_name inside02 --width 540 --height 540

```
