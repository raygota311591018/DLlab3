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
### val_set_size, lora hyperparams
  No need to change.

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
  We need to transform original csv/xlsx/txt file to a specific json form, TA had already provide a python execution file for transforming AI.xlsx file, However, we have to write own own python file if we want to do the same thing on a different form file. Using basic 10000 questions provided on Kaggle is enough. However, after adding NTU alpaca data recommended by TA ( and later updated on Kaggle ), the overall accuracy can enhance by 10~15%. which is way better than the previous one.
  
## Result
  Just as I said, I spending almost a week to finishing training since I give a extremely large epoch, the final result fell between 35~45% (don't know if I want to train again), I regard it as a huge success.
  
## Comment
  The experience during this lab is way better than previous because the loading of GPU resource is finally released, and the bug is less comparing to other two homework. I'm glad I finally finishing the course, god blessing.
