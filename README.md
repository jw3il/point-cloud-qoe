# Point Cloud Sequence QoE Dataset 

This repository contains the results of a user study on the quality of experience of point cloud sequences.
Details can be found in the corresponding publication (see references).

## Data Description

The results of the study are provided by two files `participants.csv` and `ratings.csv`. 
We further provide details about the resource requirements with `resources.csv`.
The following sections describe their content and the used data types.

### Participants

The table `participants.csv` contains the following information about each participant of the user study:

| Column Name                          | Data Type | Description                                                                                                                                                           |
|--------------------------------------|-----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `participant`                        | Int       | Participant ID                                                                                                                                                        |
| `gender`                             | String    | Gender with the options: `female`, `male`, `diverse`, `omit` (prefer not to say)                                                                                      |
| `age`                                | String    | Age, grouped by ranges (e.g. `22-23`)                                                                                                                                 |
| `screen_type`                        | String    | Options for used device type and screen size: `smartphone` (up to 7"), `tablet` (up to 12"), `laptop` (up to 18"), `pc` (up to 38"), `tv` (greater than 38"), `other` |
| `screen_avail_width`                 | Int       | `screen.availWidth` from browser                                                                                                                                      |
| `screen_avail_height`                | Int       | `screen.availHeight` from browser                                                                                                                                     |
| `screen_width`                       | Int       | `screen.width` from browser                                                                                                                                           |
| `screen_height`                      | Int       | `screen.height` from browser                                                                                                                                          |
| `experience_games_regular_screen`    | Bool      | Participant has experience in "Playing video games on regular monitors / TVs"                                                                                         |
| `experience_games_smartphone`        | Bool      | Participant has experience in "Playing video games on handheld consoles and smartphones"                                                                              |
| `experience_games_vr`                | Bool      | Participant has experience in "Playing video games on a virtual reality (VR) headset"                                                                                 |
| `experience_360_interaction`         | Bool      | Participant has experience in "Interacting with a 360 degree video"                                                                                                   |
| `experience_point_cloud_interaction` | Bool      | Participant has experience in "Interacting with point clouds"                                                                                                         |
| `experience_computer_graphics`       | Bool      | Participant has experience in "Computer graphics (a subarea of computer science)"                                                                                     |
| `first_object`                       | String    | The first point cloud object presented to the participant (`dancer` or `thaidancer`)                                                                                  |
| `duration_total`                     | Int       | Total time (in milliseconds) spent for the study, including time for feedback                                                                                         |
| `duration_introduction`              | Int       | Time (in milliseconds) spent in the introduction                                                                                                                      |
| `duration_reference_1`               | Int       | Time (in milliseconds) spent watching the first reference video (see `first_object`)                                                                                  |
| `duration_reference_2`               | Int       | Time (in milliseconds) spent watching the second reference video                                                                                                      |

### Ratings

The table `ratings.csv` contains the quality ratings of each participant for each of the 120 experiment configurations:

| Column Name                | Data Type | Description                                                                                              |
|----------------------------|-----------|----------------------------------------------------------------------------------------------------------|
| `participant`              | Int       | ID of the participant who submitted this rating                                                          |
| `object`                   | String    | Shown object, is either `dancer` or `thaidancer`                                                         |
| `distance`                 | String    | Distance of the camera to the object in `near` (2.5 units), `medium` (4.5 units), `far` (8.5 units)      |
| `frame_rate`               | Int       | Frame rate in `10`, `15`, `30`                                                                           |
| `encode_method`            | String    | Used encoding method, either `Draco` or (frame-by-frame) `V-PCC`                                         |
| `quantization_level_index` | Int       | Quantization level index from `0` (high compression, low quality) to `4` (low compression, high quality) |
| `qoe`                      | Int       | Quality rating in `1` (bad), `2` (poor), `3` (fair), `4` (good), `5` (excellent) for this configuration  |
| `duration`                 | Int       | Time (in milliseconds) spent watching this experiment configuration                                      |
| `size`                     | Int       | Video size in the browser (attribute `height` of the square-shaped `video` HTML element)                 |
| `order`                    | Int       | Ordering of the experiments for each participant from `0` to `119`                                       |

### Resources

The table `resources.csv` contains encoding and decoding time together with the bit rate of the original and compressed streams.
Note that the user study was restricted to object rate 30 for Draco.

| Column Name                | Data Type | Description                                                                                              |
|----------------------------|-----------|----------------------------------------------------------------------------------------------------------|
| `object`                   | String    | Object type, either `dancer` or ``thaidancer                                                             |
| `encode_method`            | String    | Used encoding method, either `Draco` or (frame-by-frame) `V-PCC`                                         |
| `quantization_level_index` | Int       | Quantization level index from `0` (high compression, low quality) to `4` (low compression, high quality) |
| `object_rate`              | Int       | Number of object per seconds in the sequence                                                             |
| `encoding_time`            | Float     | Encoding time per second of point cloud stream in seconds                                                |
| `decoding_time`            | Float     | Decoding time per second of point cloud stream in seconds                                                |
| `bit_rate`                 | Float     | Bit rate of the uncompressed point cloud sequence in MBit/s                                              |
| `compressed_bit_rate`      | Float     | Bit rate of the compressed point cloud sequence in MBit/s using the configuration from this row          |


## Overview and QoE Models

This repository contains jupyter notebooks that provide an overview of the data ([`qoe_overview.ipynb`](qoe_overview.ipynb)) and create qoe models using various classical machine learning methods ([`qoe_model.ipynb`](qoe_model.ipynb)).
Although the models have a fixed random state, we noticed that the results can differ slightly between different systems.

The code has been tested with Python 3.11.3, the requirements are in `requirements.txt`.

## Reference

If you use material provided in this repository, please cite it with

```
Add reference
```
