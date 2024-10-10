# sign_Langauge_Detection
Custom sign language setection using OpenCV and Medipipe

# How to run the code :

0. Run the requirement.txt file
1. In collect_images.py file change the value (number_of_classes) to add the desired number of classes you want and you can       also change the number of images that you want to collect in (dataset_size).
2. change the directory of 
    1. data (it will be create if not created)
    2. data.pickle
    3. model.p
3. In infrerence_classifier.py change
    labels_dict = {0: 'i_love_you', 1: 'Thank_you', 2: 'No'}
    to give it proper name and labeing as per choice,
    also you have to change the number of files you have to label.
4. Test images are not provided.

The way to run all the files in order:
1. collect_images.py
2. create_dataset.py
3. train_classifier.py
4. inference_classifier.py
