# Retraining and running inception V3 with a pipenv setup

Assembled from various tutorials, and configured them so they can be simply run from a pipenv shell.
For more info, see tensorflow website:
 https://www.tensorflow.org/tutorials/image_retraining

## To set up

- clone of this repo

- run `pipenv install`to install requirements, including tensorflow (assuming you have python3 and pipenv installed)

- Open a pipenv shell (by typing `pipenv shell`)

## To retrain:

use retrain.py by running something like:

python3 -m retrain --bottleneck_dir=./tf_files/bottlenecks --how_many_training_steps=1000 --model_dir=./tf_files/models/ --summaries_dir=./tf_files/training_summaries/ --output_graph=./tf_files/retrained_graph.pb --output_labels=./tf_files/retrained_labels.txt --image_dir=./myData --architecture='inception_v3'

Assuming ./myData contains the images to to use for re-training. Each category of image needs to be placed in its own folder:
./myData/category1
./myData/category2
./myData/category3 
...etc.

## To use the classifier, run:

python3 -m label_image --graph=./tf_files/retrained_graph.pb  --image=./myExtraPic.jpg --labels=./tf_files/retrained_labels.txt
