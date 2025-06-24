MIGraphX EP INT8 Inference on Inception V3 model

There's ways to perform an inference here. First we can generate calibration data using the ROCm Execution provider and then save out the table using the onnxruntime toolset so the MIGraphX EP can use the result for quantization. The second way is to allow MIGraphX to run the inference for calibration while also then setting the EP into int8 mode to load in the new calibration data.

The script is using ILSVRC2012 ImageNet dataset for calibration and prediction.
Please prepare the dataset as below, 
1. Create dataset folder 'ILSVRC2012' in workspace.
2. Download ILSVRC2012 validation dataset and development kit from http://www.image-net.org/challenges/LSVRC/2012/downloads.
3. Extract validation dataset JPEG files to 'ILSVRC2012/val'.
4. Extract development kit to 'ILSVRC2012/devkit'. Two files in the development kit are used, 'ILSVRC2012_validation_ground_truth.txt' and 'meta.mat'.
5. Download 'synset_words.txt' from https://github.com/HoldenCaulfieldRye/caffe/blob/master/data/ilsvrc12/synset_words.txt into 'ILSVRC2012/'.


The model leverages torchvision pretrained models to pull down and genearate an inceptionV3 model with the latest pretrained weights.

In the e2e_migraphx_inceptionV3_example.py script, you'll need to also set the proper location for the dataset for calibration data

