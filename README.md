# Deep Learning Lab3 Report
  This time we're asked to fine-tuning Alpaca-Lara model to adapt the Chinese mutiple choice task.
  
## Fine-Tuning
  below is a list for the parameters I changed:
  
### base_model:
  we can only choose llama-7b-hf due to the limitation of GPU RAM.
### data_path, output_dir:
  we don't need to discuss this isn't it?
### batch_size, micro_batch_size:
  I set these to 128, 4 just as TA does, and it works fine.
### num_epochs:
  I set to 20 and then 30 since everyone has its own GPU provided by NYCU, nobody will ever blame me for using GPU, so I just occupy like, whole week continuously. :)
### learning_rate:
  No need to change.
### cutoff_len
  Here comes the interesting part. I set to 512(default) first time and the result crashed. the machine can only repeat the first two words of my question, later I knew that this parameter is about how much token you can look in a training data, and fortunately I found a website that can estimate how much token will be used in a training data. I put in the longest question and it shows about 3000~4000, so I set cutoff to 4096 and it works.
### val_set_size

### lora hyperparams
  No need to change.
### llm hyperparams


  And the following shows the parameters I can change when using model user interface.
  
### Temperature
  Controls the variation of output. Since we only need a number, so smaller is better.
### Top p
  Kick out the output candidate if its probability exceeds top_p's value, if the parameter is bigger, the variation become smaller but enhence the accuracy. I set it to 0.75 same as TA does.
### Top k
  Limiting the token amount, only preserve "top_k" possible token. if the parameter is smaller, variation become smaller, too. Set it as small as possible.
### Beams
  Search size, bigger is better.
### Max tokens
  Longest token of output, set it smaller since we only need number.
  
## Training Data
  
  
## Result
  the error rate I get is about 7.3 to 6.7, depend on the learning epoch. The accuracy keep increasing when the epoch getting larger, but I choose to stop at 115 epoch due to the problem that too much students keep using gpu.
  I train under two case, one with data argumentation(noise data + original data), and one without it(noise data only). the result is quite strange: It seems that the error rate between two case isn't very obvious, which is different from TA's showcase.
  
## Comment
  The main problem isn't the machine learing model itself, THE AMOUNT OF GPU IS TOO SMALL. We have to check the gpu frequently in order to train our model(also prevent other students using it and delay your training for 2 days), and this bother me so much because I have to keep checking terminal, I stay up almost every night during the competetion. this is a very awful experience. Please, please try apply some public gpu resource from university next time, I sincerely begging you guys.
