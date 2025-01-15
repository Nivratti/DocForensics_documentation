# Model Fine-Tuning

## Fine-Tuning Document Tampering Localization model:

You can fine-tune the forensics model for the following purposes:

1. **Adding Support for New Card Types**: Extend the model's capabilities to handle previously unsupported card types by training it on new datasets specific to those cards.

2. **Improving Performance on Existing Card Types**: Enhance the accuracy and reliability of tampering detection for currently supported card types by fine-tuning the model with additional high-quality data.

### Dataset Requirements:

To enhance support for new card types, ensure you collect authentic **at least 30 unique, high-quality images** of the new card type.

### Tutorials

Watch the video tutorial on fine-tuning the document forensic model:

- [Google Drive Link](https://drive.google.com/file/d/1ZeHLxIoqGcjD5GMREQUL9em7FBiDgSY4/view?usp=drive_link)  
- [GitHub Release Link](https://github.com/Nivratti/doc_forensics_train/releases/download/v4.0/Finetuning-Document-forensic-model.mp4)

### Steps:

#### Step 1: Crop ID cards
Crop ID cards to isolate the ID card region from the background, retaining only the ID card region. The current card segmentation model supports PAN cards and Mauritius ID cards. For other card types, you can either search for a pre-trained model online or manually crop the ID card region.

##### Command Line Usage

This section explains how to use the `inference_card_segmentation.py` script from the command line.

Download the `card_segmentation.zip` file from the following link: [card segmentation model](https://github.com/Nivratti/doc_forensics_train/releases/tag/v4.0)

After downloading, extract the contents into the `./resources/models` folder. Once extracted, the model path will be:  
```bash
./resources/models/card_segmentation/v8.0.1/best.onnx
```

###### General Syntax
```bash
python inference_card_segmentation.py \
   --input_dir "<path_to_input_directory>" \
   --output_dir "<path_to_output_directory>"
```

- **`--input_dir`**: Path to the folder containing input files (e.g., raw ID card images).
- **`--output_dir`**: Path to the folder where processed outputs will be saved.

###### Example

1. Processing Mauritius ID Cards
   ```bash
   python inference_card_segmentation.py \
      --input_dir "datasets/raw/Mauritius-id-nic-v1" \
      --output_dir "datasets/processed/Mauritius-id-card/card-det-res"
   ```

#### Step 2: Orientation correction
Correct the orientation of the ID card images, if necessary, to ensure they are upright and properly aligned.

#### Step 3: Split the Dataset

Split the collected images into training and validation sets, using an 80:20 ratio as a default or another ratio of your choice. This means 80% of the images will be used for training, while the remaining 20% will be used for validation. You can create folders named `train` and `val` to store the respective data.

#### Step 4: Generate tampering dataset

Generate a tampering dataset by running the data generation script. Ensure to run the script separately for the training and validation sets.

The input for the script will be the cropped and split datasets you have prepared earlier. It will produce a tampered image and a corresponding mask for every original image.

For each original image, it generates three outputs with specific postfixes added to the filenames:

1. Original Image: with `_orig.jpeg` postfix.  
2. Tampered Image: with `_tampered.jpeg` postfix.  
3. Mask: with `_mask.png` postfix.

For example, the output files will follow this naming convention:

- `11_orig.jpeg`, `11_tampered.jpeg`, `11_mask.png`
- `12_orig.jpeg`, `12_tampered.jpeg`, `12_mask.png`
- `13_orig.jpeg`, `13_tampered.jpeg`, `13_mask.png`

##### Command Line Usage
Use the following syntax and examples to run the script from the command line.

###### General Syntax
```bash
python data_gen_wrapper.py 
   --source_dir "<path_to_source_directory>" \
   --out_dir "<path_to_output_directory>"
```

- **`--source_dir`**: Path to the source directory containing the cropped and split datasets (e.g., training or validation sets).
- **`--out_dir`**: Path to the output directory where the tampered images and masks will be saved.

###### Example Commands
1. For generating Training Dataset
   ```bash
   python data_gen_wrapper.py \
      --source_dir "./datasets/processed/Mauritius-id-card/split_cropped/train/" \
      --out_dir "./datasets/data_gen/Mauritius-id-card/train"
   ```

2. For generating Validation Dataset
   ```bash
   python data_gen_wrapper.py \
      --source_dir "./datasets/processed/Mauritius-id-card/split_cropped/val/" \
      --out_dir "./datasets/forensic_data_gen/Mauritius-id-card/val"
   ```

By running these commands, tampered images and their corresponding masks will be generated and stored in the specified output directories.

#### Step 5: Run Model Fine-Tuning Script

To fine-tune the model, execute the provided `main.py` script from the command line. This script will fine-tune your model using the specified training and testing datasets.

##### Command Line Usage

###### General Syntax
```bash
python main.py \
    --data_path "<path_to_training_data>" \
    --test_data_path "<path_to_testing_data>" \
    --output_dir "<path_to_model_output>" \
    --weights_path "<path_to_weights_file>"
```

- **`--data_path`**: Path to the folder containing the training dataset (e.g., images and masks).
- **`--test_data_path`**: Path to the folder containing the testing dataset for evaluation during fine-tuning.
- **`--output_dir`**: (Optional) Path to the directory where the fine-tuned model and logs will be saved.
- **`--weights_path`**: (Optional) Path to the pre-trained weights file. The default value is `./ckpt/v8.0/best_model.pth`. You can change this path based on your requirements.

To download the `v8.0/best_model.pth` file use the following link: [v8.0/best_model.pth](https://github.com/Nivratti/DocForensics_Mauritius_Inference/releases/download/v8.0/best_model.pth)

##### Example Command
```bash
python main.py \
    --data_path "./datasets/data_gen/Mauritius-id-card/train/" \
    --test_data_path "./datasets/data_gen/Mauritius-id-card/val/" \
    --output_dir "./output/training/v8.1" \
    --weights_path "./ckpt/v8.0/best_model.pth"
```

##### Output
- `Fine-Tuned Model`: The updated model file will be saved in the specified `--output_dir`.
- `Fine-Tuning Logs`: Logs containing metrics such as loss, accuracy, and validation performance will be saved for further analysis.

##### Notes
1. Ensure that the directories specified in `--data_path` and `--test_data_path` contain the correctly prepared datasets.
2. If you have specific pre-trained weights to use, provide the path using `--weights_path`. Otherwise, the default weights file will be used.
3. The `--output_dir` should be an empty or new directory to avoid overwriting existing files.

#### Step 6: Export model

Once the fine-tuning process is complete, the trained PyTorch model can be exported to the *ONNX (Open Neural Network Exchange)* format for compatibility with other frameworks or deployment environments.

##### Command Line Usage

###### General Syntax
```bash
python export.py --weights_path "<path_to_trained_model_weights>" --onnx_output_path "<path_to_save_onnx_model>"
```

- *`--weights_path`*: Path to the trained PyTorch model file (e.g., `.pth` file) that you want to export.
- *`--onnx_output_path`*: Path where the exported ONNX model will be saved.

##### Example Command
```bash
python export.py \
  --weights_path "./output/training/v8.2/best_model.pth" \
  --onnx_output_path "./output/training/v8.2/best_model.onnx"
```

##### Output
- *ONNX Model File*: The exported ONNX model will be saved at the location specified by `--onnx_output_path`.

##### Notes
1. Ensure the `--weights_path` points to the correct and finalized PyTorch model file from the fine-tuning step.
