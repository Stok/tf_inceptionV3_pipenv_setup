I assembled .py files from various tutorials, and configured them so they can be simply run from a pipenv shell.

To train, run something like:

python3 -m retrain --bottleneck_dir=./tf_files/bottlenecks --how_many_training_steps=1000 --model_dir=./tf_files/models/ --summaries_dir=./tf_files/training_summaries/ --output_graph=./tf_files/retrained_graph.pb --output_labels=./tf_files/retrained_labels.txt --image_dir=./myData --architecture='inception_v3'


To make predictions, run:

python3 -m label_image --graph=./tf_files/retrained_graph.pb  --image=./myExtraPic.jpg --labels=./tf_files/retrained_labels.txt
