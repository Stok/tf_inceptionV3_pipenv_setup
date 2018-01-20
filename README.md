# Retraining and running inception V3 with a pipenv setup

I assembled .py files from various tutorials, and configured them so they can be simply run from a pipenv shell.

To prepare the requirements (assuming you have python3 and pipenv installed):
pipenv install

This should install tensorflow.
Then to train, run something like:

python3 -m retrain --bottleneck_dir=./tf_files/bottlenecks --how_many_training_steps=1000 --model_dir=./tf_files/models/ --summaries_dir=./tf_files/training_summaries/ --output_graph=./tf_files/retrained_graph.pb --output_labels=./tf_files/retrained_labels.txt --image_dir=./myData --architecture='inception_v3'

Assuming ./myData contains the images to to use for re-training. Each category of image needs to be placed in its own folder:
./myData/category1
./myData/category2
./myData/category3 
...etc.

To make predictions, run:

python3 -m label_image --graph=./tf_files/retrained_graph.pb  --image=./myExtraPic.jpg --labels=./tf_files/retrained_labels.txt
