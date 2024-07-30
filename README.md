# SAM2-Video-Predictor

[![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/MJAHMADEE/SAM2-Video-Predictor/blob/main/LICENSE)
[![GitHub stars](https://img.shields.io/github/stars/MJAHMADEE/SAM2-Video-Predictor.svg)](https://github.com/MJAHMADEE/SAM2-Video-Predictor/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/MJAHMADEE/SAM2-Video-Predictor.svg)](https://github.com/MJAHMADEE/SAM2-Video-Predictor/network)

## Video segmentation with SAM 2

This repository provides tools and examples for using SAM 2 for interactive segmentation in videos. It covers the following:

- Adding clicks on a frame to get and refine _masklets_ (spatio-temporal masks)
- Propagating clicks to get _masklets_ throughout the video
- Segmenting and tracking multiple objects simultaneously

### Terminology

- _Segment_ or _mask_: The model's prediction for an object on a single frame.
- _Masklet_: Spatio-temporal masks across the entire video.

### Installation

To use SAM 2, install `segment-anything-2` in your environment. Follow the [installation instructions](https://github.com/facebookresearch/segment-anything-2#installation) from the official repository.

#### Required Packages

Ensure you have `jupyter` and `matplotlib` installed to run the example notebooks.

### Download Checkpoints

First, download the model checkpoints. You can download all checkpoints by running the provided script, or individually from the following links:

- [sam2_hiera_tiny.pt](https://dl.fbaipublicfiles.com/segment_anything_2/072824/sam2_hiera_tiny.pt)
- [sam2_hiera_small.pt](https://dl.fbaipublicfiles.com/segment_anything_2/072824/sam2_hiera_small.pt)
- [sam2_hiera_base_plus.pt](https://dl.fbaipublicfiles.com/segment_anything_2/072824/sam2_hiera_base_plus.pt)
- [sam2_hiera_large.pt](https://dl.fbaipublicfiles.com/segment_anything_2/072824/sam2_hiera_large.pt)

### Loading the SAM 2 Video Predictor

#### Select an Example Video

Assume the video is stored as a list of JPEG frames with filenames like `<frame_index>.jpg`. For custom videos, you can extract their JPEG frames using ffmpeg:

```sh
ffmpeg -i <your_video>.mp4 -q:v 2 -start_number 0 <output_dir>/'%05d.jpg'
```
#### Adding Objects to a Frame

SAM 2 can segment and track multiple objects simultaneously. It is more efficient to batch them together to reduce computation costs.

1. **Add the first object** (e.g., a child's shirt) with a **positive click** at (x, y) = (200, 300) on frame 0. Assign it to object id `2`.

2. **Refine the prediction** with a **negative click** at (x, y) = (275, 175) to get the desired mask.

3. **Add the second object** (e.g., another child's shirt) with a positive click at (x, y) = (400, 150) on frame 0. Assign it to object id `3`.

#### Propagate Prompts to Get Masklets

Propagate the prompts for both objects to obtain their masklets throughout the video.

### Usage

Now you can try SAM 2 on your own videos and use cases. Detailed examples and step-by-step instructions are provided in the example notebook.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

Special thanks to the [Facebook Research](https://github.com/facebookresearch) team for their work on SAM 2.



This `README.md` includes essential information about the project, installation instructions, usage, and hyperlinks to resources, enhancing its readability and accessibility. &#8203;:citation[oaicite:0]{index=0}&#8203;

