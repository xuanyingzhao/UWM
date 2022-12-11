# Semantic segmentation

### Introduction
It may be used to train, validate and tune deep learning models for image segmentation. The following directory structure is assumed:
```
├── code (source code)
├── input (dataset)
└── output (working directory)
```

The dataset should have images inside a directory named `train` and a CSV file named `train.csv`. An example is shown below:

```
input
├── train.csv
└── train
    ├── slice_0001_266_266_1.50_1.50.png
    ├── slice_0002_266_266_1.50_1.50.png
    ├── slice_0003_266_266_1.50_1.50.png
```

The CSV file is expected to have class labels under a column named `class` and mask annotations under `segmentation` as in the example below:

```
id,class,segmentation
case123_day20_slice_0065,large_bowel,
case123_day20_slice_0065,small_bowel,
case123_day20_slice_0065,stomach,28094 3 28358 7 28623 9 28889 9 29155 9 29421 9 29687 9 29953 9 30219 9 30484 10 30750 10 31016 10 31282 10 31548 10 31814 10 32081 9 32347 8 32614 6
```

The annotations are assumed to be run length encoded (RLE) masks.

### To use this repo with Luminide
- Accept [competition rules](https://www.kaggle.com/competitions/uw-madison-gi-tract-image-segmentation/rules).
- Attach a Compute Server that has a GPU (e.g. gcp-t4).
- Configure your [Kaggle API token](https://github.com/Kaggle/kaggle-api) on the `Import Data` tab.
- On the `Import Data` tab, choose Kaggle Competition Data and then enter `uw-madison-gi-tract-image-segmentation`.
- Train a model using the `Run Experiment` menu.

### Kaggle submission
- Upload the code to Kaggle as a dataset by using the Run Experiment menu (select `Custom > kaggle.sh`).
- To create a submission, copy [kaggle.ipynb](kaggle.ipynb) to a new Kaggle notebook.
- Add the notebook output of `https://www.kaggle.com/luminide/wheels3` as Data.
- Add your dataset at `https://www.kaggle.com/<kaggle_username>/kagglecode1` as Data.
- Add the relevant competition dataset as Data.
- Save the notebook after turning off the `Internet` setting and turning on the GPU.
- Submit the results and wait for the notebook to finish.
- Check the [leaderboard](https://www.kaggle.com/competitions/uw-madison-gi-tract-image-segmentation/leaderboard) to see your score!

### Additional features
- Use the `Experiment Tracking` menu to track experiments.
- To tune the hyperparameters, edit [sweep.yaml](sweep.yaml) as desired and launch a sweep from the `Run Experiment` tab. Tuned values will be copied back to a file called `config-tuned.yaml` along with visualizations in `sweep-results.html`.
- To use the tuned hyperparameter values, copy them over to `config.yaml` before training a model.
- For exploratory analysis, run [eda.ipynb](eda.ipynb).
- To monitor training progress, use the `Experiment Visualization` menu.
- After an experiment is complete, use the file browser on the IDE interface to access the results on the IDE Server.
- To generate a report on the most recent training session, run report.sh from the `Run Experiment` tab. Make sure `Track Experiment` is checked. The results will be copied back to a file called `report.html`.


For more details on usage, see [Luminide documentation](https://luminide.readthedocs.io)
