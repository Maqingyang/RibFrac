## Usage

### Install Required Packages
First install required packages in [`requirements.txt`](requirements.txt) using pip:
```bash
pip install -r requirements.txt
```
### Training
To train the FracNet model, run the following in command line:
```bash
python -m main --train_image_dir <training_image_directory> --train_label_dir <training_label_directory> --val_image_dir <validation_image_directory> --val_label_dir <validation_label_directory>
```

### Prediction
To generate prediction, run the following in command line:
```bash
python -m predict --image_dir <image_directory> --pred_dir <predition_directory> --model_path <model_weight_path>
```

In the [predict.py](predict.py), we adopt a post-processing procedure of [removing low-probability regions](predict.py#L18), [spine regions](predict.py#L24), and [small objects](predict.py#L48). This procedure leads to fewer false negatives. You may also skip the post-processing by setting `--postprocess False` in the command line argument and check the raw output.

### Evaluation
To evaluate your prediction, run the following in command line:
```bash
python -m ribfrac.evaluation --gt_dir <gt_directory> -pred_dir <prediction_directory> --clf False
```
