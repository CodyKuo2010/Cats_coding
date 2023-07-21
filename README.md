# pet_identifier

Have AI differentiate your pets using this code! All you need are pictures and to follow a few simple steps. You will need **imagenet** from **jetson_inference**.

![pet cat with accuracy](https://imgur.com/a/X6jv4Up)

## The Algorithm

Add an explanation of the algorithm and how it works. Make sure to include details about how the code works, what it depends on, and any other relevant info. Add images or other descriptions for your project here. 

## Running this project

1. Make sure that you have a sufficient amount of pictures per pet, you will need a lot of them. Make directories under my_pets which is in jetson_inference -> python -> training -> classification -> data. You need all pictures to be in jpg form. Make sure you don't have class imbalance(you need an even amount of pictures in each directory).
2. Make 3 directories per pet, one under val, one under train, one under test. Upload images to each directory(you can use the same pictures for each directory, though different pictures are better). 
3. Find labels.txt and change the labels to your pets' names. If your directories were capitalized, make sure these names are also. Use ctrl+S to save.
4. Find the my_pets directory under classification. Open a terminal and cd to my_pets. Run this command: imagenet.py --model=$NET/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=$DATASET/labels.txt $DATASET/test/**(your pet here)**/**(image name here)**.jpg **(new name for image)**.jpg. It will print out your image, idenitfying the class and confidence. The more pictures you took, the higher the confidence will be.
5. You will need the jetson_inference library.

[View a video explanation here](video link)
