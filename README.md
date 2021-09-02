# Name_Calling
SRIB-PRISM Program : 
First of all, we would like to thank the whole Samsung PRISM team for providing us this great opportunity. This program really helped us to know that how can we implement our learnings in a real-life project and also motivated us to learn more & more in this field. Dealing with audio data were totally new for our team but with hard and group work,  we were able to complete the task effectively. We strongly thanks our mentor for his continuous guidance which helps us in tackling with the difficulties we were facing during the development phase. They were very supportive and knowledgeful.

## Problem Statement
**Name Calling :-**  You are listening music using headphone and someone calls your name multiple times but you are not able to listen due to high volume. So is it possible to solve the problem? If phone can detect that someone is calling you, then hectic feedback or volume can be reduced to enable you to attend the person. You need to work on the audio files directly without converting speech to text or ASR techniques are not allowed.

## Proposed Method
To tackle this problem, we proposed the following method -
1. First, a training and validation dataset is prepared using the below mentioned ways.
2. We tried to preprocess the data by extracting the important features from the wav audio file as we were not supposed to use the ASR techniques.
3. We extracted the mel-spectrogram features from the audio files and then after some more preprocessing, converted the wav files to 2-D numpy arrays (training-validation data-label arrays).
4. We used the Siamese CNN network to learn these acoustic embeddings. As the siamese network contain two (or more) identical subnetworks, so to train this siamese network we need to have positive pairs and negative pairs.
5. We used the euclidean distance to calculate the distance between two volumes inside of a CNN.
6. Finally, trained the siamese network using these training image pairs and validated using validation image pairs.
7. The accuracy, loss and other major parameters were keenly observed and suitable threshold point is calculated.

## Dataset
#### Dataset Path & Contents 
1. The whole dataset comprises of total 1260 wav files and divided into training and testing files. The dataset folder comprises of two files -
      1. train_wav - It contains total of 1000 training files with 20 name variations and each name variation has 50 files.
      2. test_wav - It contains total of 260 validation files with 20 name variations and each name variation has 13 files. 
2. The following 20 name variations are used for the training and testing purpose -
           "abhishek anmol anurag deewanshu himanshu kishan mayank narender neeraj prince ritvik sayan shiv shreyas shubham siddharth sourav swaraj utkarsh vikrant"
3. The file are titled as the same name recorded in the file and saved in wav format. For example : "abhishek001.wav", "abhishek002.wav", "anmol001.wav" etc.

#### Collection Strategy
1. Each training and testing files are manually recorded by using our mobile recorder. 
3. Each file contains a single name recorded in it and each file duration is around 1 second.
4. Finally, each file is saved into the wav format.

## Model 
#### Siamese Model Architecture
<p align="center">
  <img width="400" height="400" src="https://media.github.ecodesamsung.com/user/9381/files/aa341500-bfc3-11eb-94a6-bf8cb21432a2">
</p>

Siamese networks are a special class of neural network:
1. Siamese networks contain two (or more) identical subnetworks.
2. These subnetworks have the same architecture, parameters, and weights.
3. Any parameter updates are mirrored across both subnetworks, meaning if you update the weights on one, then the weights in the other are updated as well.

Below shown is the basic CNN model summary:
<p align="center">
  <img width="400" height="400" src="https://media.github.ecodesamsung.com/user/9382/files/a7402100-bfd1-11eb-8c3f-70978239f788">
</p>

#### Accuracy v/s Epochs Plot
The Training-Validation Accuracy v/s Epochs Plot is as follows:
<p align="center">
  <img width="400" height="300" src="https://media.github.ecodesamsung.com/user/9382/files/5e886800-bfd1-11eb-89f8-8ecc77ba2c2b">
</p>

#### Loss v/s Epochs Plot
The Training-Validation Loss v/s Epochs Plot is as follows:
<p align="center">
  <img width="400" height="300" src="https://media.github.ecodesamsung.com/user/9382/files/97284180-bfd1-11eb-9332-18cd349150fc">
</p>

#### Model Performance Metrics
The performance metrics obtained are as follows:
<p align="center">
  <img width="700" height="150" src="https://media.github.ecodesamsung.com/user/9381/files/ab1f7380-bfd0-11eb-986b-4ff9d95b6637">
</p>

## Scripts
#### Training and Validation
This folder contains the trraining-validation file in two formats i.e .py & .ipynb (can use anyone as per your wish). Although we have well documented our python notebook, here we have just written the overview how to run the python file -
1. Carefully read the above dataset rules to create your own dataset.
2. We have implemented our code to accept the files with having their titles as the name present in the file with three digit number at the end and saved in wav format.
3. After that, update the following variables in the notebook :
      1. path_to_train_wav -> folder path where training dataset is present
      2. path_to_test_wav -> folder path where validation datset is present
4. Then, run the notebook to see the model training and the metrics calculated on the validation dataset.

#### Test (For testing your golden dataset)
This folder contains the test file in two formats i.e .py & .ipynb (can use anyone as per your wish) and two text file (one is the inputtxt & second is outputtxt file)-
1. These files are for the testing purpose for your own golden dataset.
2. It accepts a input.txt file and updates the output.txt file with the prediction values for the same.
3. The input.txt file should have three column values i.e serial_no, reference_wav_path and query_wav_path but it doesn't expects these column headers.
4. Also, the output.txt file contains two column values i.e serial_no and predicted_value.
5. In the test file, update the following variables -
      1. path_to_model -> model location
      2. path_to_input_txt -> input.txt location
      3. path_to_output_txt -> output.txt location
6. Finally, run the python script to see the output results.

## Android Application
"Congruent" named apk is also uploaded associated with this project. Kindly ignore the warnings and allow permissions while installing it in your mobile with SDK version greater than 26 (Android Oreo). 
Following are the intrustion to use our application:
1. 1st record reference audio wav file of 1 second.
2. Automatically your navigation page will update for you to record Query audio wav file.
3. Press Record_button to record the Query audio wav file of 1 second.
4. Play your files before submitting(Button) in the recorder_list(Button) to get optimum results.
5. Reset Button will ask you to again record reference file following with the Querry file in case of failure.

Note: Submit Button is not functional at this point of time where the app will return distance score between the two audio files.

## Meet the Team 
Team Congruent:
  1. Swaraj Gupta (swaraj.gupta217@gmail.com)
  2. Shiv Jaiswal (shivjaiswal2000@gmail.com)
  3. Mayank Goyal (goyalmayank522@gmail.com)

If opening the files gives you any difficulty or if you have any kind of suggestions, please let us know.
