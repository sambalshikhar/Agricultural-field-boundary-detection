# Spatio-Temporal Attention-based Unet for Field Boundary Detection

![](https://github.com/sambalshikhar/Agricultural-field-boundary-detection/blob/7dd510f3cbc2319c99556d16d2d7f61e93c51c3a/Screenshot%20from%202023-04-01%2018-18-09.png)

![](https://github.com/sambalshikhar/Agricultural-field-boundary-detection/blob/7dd510f3cbc2319c99556d16d2d7f61e93c51c3a/Screenshot%20from%202023-04-01%2018-18-19.png)

## Get Started With Inferencing

First clone this Git repository.

```bash
git clone https://github.com/radiantearth/model_nasa_rwanda_field_boundary_competition_gold.git
cd model_nasa_rwanda_field_boundary_competition_gold/
```

After cloning the model repository, you can use the Docker Compose runtime
files as described below.

## Pull or Build the Docker Image

Pull pre-built image from Docker Hub (recommended):

```bash
docker pull docker.io/radiantearth/model_nasa_rwanda_field_boundary_competition_gold:1
```

Or build image from source:

```bash
docker build -t radiantearth/model_nasa_rwanda_field_boundary_competition_gold:1 -f Dockerfile .
```

## Run Model to Generate New Inferences

1. Prepare your input and output data folders. The `data/` folder in this repository
    contains some placeholder files to guide you.

    * The `data/` folder must contain:
        * `input/`: input folder containing the tile imagery.
            This folder has the following naming convention: 
            `{dataset_id}_{tile_id}_{year}_{month}`. For example, for a dataset_id (`nasa_rwanda_field_boundary_competition`), a tile_id (`00`) and a year (`2021`), we'll have the following structure:
            ```
                nasa_rwanda_field_boundary_competition_source_test_00_2021_03/
                nasa_rwanda_field_boundary_competition_source_test_00_2021_04/
                nasa_rwanda_field_boundary_competition_source_test_00_2021_08/
                nasa_rwanda_field_boundary_competition_source_test_00_2021_10/
                nasa_rwanda_field_boundary_competition_source_test_00_2021_11/
                nasa_rwanda_field_boundary_competition_source_test_00_2021_12/
            ```
            Notice that the months are fixed and have to be : ['2021_03', '2021_04', '2021_08', '2021_10', '2021_11', '2021_12'].

        * The `output/` folder is where the model will write inferencing results.

2. Set `INPUT_DATA` and `OUTPUT_DATA` environment variables corresponding with
    your input and output folders. These commands will vary depending on operating
    system and command-line shell:

    ```bash
    # change paths to your actual input and output folders
    export INPUT_DATA="/home/my_user/model_nasa_rwanda_field_boundary_competition_gold/data/input/"
    export OUTPUT_DATA="/home/my_user/model_nasa_rwanda_field_boundary_competition_gold/data/output/"
    export DATASET_ID="nasa_rwanda_field_boundary_competition"
    ```

3. Run the appropriate Docker Compose command for your system

    ```bash
    docker compose up model_nasa_rwanda_field_boundary_competition_gold_v1
    ```

4. Wait for the `docker compose` to finish running, then inspect the
`OUTPUT_DATA` folder for results.
