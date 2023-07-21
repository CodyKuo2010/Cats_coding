# pet_identifier

Have AI differentiate your pets using this code! All you need are pictures and to follow a few simple steps. You will need **imagenet** from **jetson_inference**.

![pet cat with accuracy](https://imgur.com/a/X6jv4Up)

## The Algorithm

Once you make your directories, train them, and export them the my_pets.py will recognize that training network. If you run the command on step 5, it will finally use this network and identify your pets. Do not have more than one pet in a picture, because the image recognition will get confused.

## Running this project

1. Make sure that you have a sufficient amount of pictures per pet, you will need a lot of them. Make directories under my_pets_train in jetson-inference -> python -> training -> classification -> data. You need all pictures to be in jpg form. Make sure you don't have class imbalance(you need an even amount of pictures in each directory).
2. Make 3 directories per pet, one under val, one under train, one under test. Upload images to each directory(you can use the same pictures for each directory, though different pictures are better). 
3. Find labels.txt and change the labels to your pets' names. If your directories were capitalized, make sure these names are also. Use ctrl+s to save.
4. Run the command ./docker/run.sh in jetson-inference. Inside the docker, go to classification folder and run the command: python3 train.py --model-dir=models/my_pets_train data/my_pets_train. You can stop this process with ctrl+c anytime. Run python3 onnx_export.py --model-dir=models/my_pets_train and exit docker with ctrl+d.
5. Find the my_pets directory under classification. Open a terminal and cd to my_pets. Run this command: imagenet.py --model=$NET/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=$DATASET/labels.txt $DATASET/test/**(your pet here)**/**(image name here)**.jpg **(new name for image)**.jpg. It will print out your image, idenitfying the class and confidence. The more pictures you took, the higher the confidence will be.
6. You will need the jetson_inference library.

[View a video explanation here](https://www.youtube.com/watch?v=k6ZOh6K1HQI)https://www.youtube.com/watch?v=k6ZOh6K1HQI)
