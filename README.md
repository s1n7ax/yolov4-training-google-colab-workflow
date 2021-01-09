# yolov4-training-google-colab-workflow
Google Colab notebook script to build the Colab environment and start training in one click.

As you may know, Google Colab environment resets after few hours. So it's
important to maintain a script that build the environment, retrieve data from
permanent storage, do all the processing stuff and backup important files back
to permanent storage. More importantly, script should be able to start from where ever
you left off in the last session. Well, that's exactly what this notebook does.

To be specific, notebook,
1. Clone, configure and build Darknet (Darknet is an open Yolo v4 implementation).
Configuration enables GPU support along with OpenCV, Cuda and cuDNN.
1. Validates Darknet build using pre-trained weights.
1. Mount Google Drive to Colab environment.
1. Retrieve training data set from "GD_DATA_ROOT_PATH" location. Note that "GD_DATA_ROOT_PATH" is relative to
the root of google drive and all the data should be in the standard Darknet
training data set format.
1. Start training the Yolo model.
1. Backup weights back to Google Drive.


# Configuration
Notebook script can be configured using variables.

* GD_DATA_ROOT_PATH - Path to root of the training data folders. Root contains
many training data sets in folders.

* GD_DATA_DIR_NAME - Name of the folder for current training session in "GD_DATA_ROOT_PATH".
All the data will be copied to the Colab session before start training. That data
will be used to train the Yolo model.

* SUBDIVISIONS - Subdivision of the Yolo network. Default: 64
YOLO_WIDTH - Yolo network width. Default: 416
YOLO_HEIGHT - Yolo network height. Default: 416

In addition to the mentioned configurations, following Yolo network configurations
will be automatically configured to the recommended values based on the information from training data.

* max_batches
* steps
* classes
* filters
