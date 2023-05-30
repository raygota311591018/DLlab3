# Deep Learning Lab2 Report
  Similar to the previous lab, the lab is about using ESPnet toolkit to train Taiwanese speech data with noise and translate it into text. The following content shows how to build and complete the task.
  
## Data Argumentation
  The training data we use is base on Taiwanese audio file from lab1. Since the testing data have distortion this time, the training data need to add some noise, too. First, I followed TA's powerpoint, by translated audio to 16k sample rate and using a python transform file, I successfully adding background and short noise on my data. To further increasing the learning accuracy, I choose to put both the original data and data with noise as training data, so the amount of audio files are about 6200, which is such a large number.
  The location of the training data is as same as what lab1 did, so i will just skip this part since it feels a ittle bit reduntant to write it down again.
  
## Training Data
  This time we're asked to use pre-train model before Espnet, I choose Wavlm as my pre-train model, and aishell as the training model. The reason is that I'm using the GPU this course provide and it's memory and computing power isn't very good, so I have no choose but using the small size model to prevent the CUDA: out of memory issue when training.
  Wavlm pre-train model asking to install two additional frankwork, which is S3prl and Fairseq. The installation oof the two framework can't be done by just using "./install_xxx.sh". Instead, it can be completed only by following the "custom tool installation" in ESPnet tutorial. The exact command is "bash -c ". activate_python.sh; ./installers/install_xxx.sh". This bother me for a long time since there is no clue guiding me here.
  Except the issue I mention above, the rest steps is quite similar to lab1, just modify run.sh file to call the right pre-train model and everything will be fine.
  The batch size I choose is extremely small because I keep getting CUDA: out of memory issue. and my epoch is from 35, 70, 80, 100, to 110.
  
## Result
  the error rate I get is about 7.3 to 6.7, depend on the learning epoch. The accuracy keep increasing when the epoch getting larger, but I choose to stop at 115 epoch due to the problem that too much students keep using gpu.
  I train under two case, one with data argumentation(noise data + original data), and one without it(noise data only). the result is quite strange: It seems that the error rate between two case isn't very obvious, which is different from TA's showcase.
  
## Comment
  The main problem isn't the machine learing model itself, THE AMOUNT OF GPU IS TOO SMALL. We have to check the gpu frequently in order to train our model(also prevent other students using it and delay your training for 2 days), and this bother me so much because I have to keep checking terminal, I stay up almost every night during the competetion. this is a very awful experience. Please, please try apply some public gpu resource from university next time, I sincerely begging you guys.
