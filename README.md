burgundy
========

Hosted on http://burgundy.io/

Generates yummy project names using one of 5 RNNs trained on this short wordlist:
https://github.com/shariq/burgundy/blob/master/wordserver/old_burgundy_words.txt

RNN code came from:
http://karpathy.github.io/2015/05/21/rnn-effectiveness/ 

======
Making your own models and wordserver
======

Hosted on http://burgundy.io:8080

Follow the guide at https://github.com/karpathy/char-rnn to set up char-rnn on your machine.

Copy the scripts in the burgundy/rnn folder into the char-rnn folder you've just set up.

Put your training data (a text file with a new word on each line) into a new directory called char-rnn/data/words. Name your text file input.txt.

Run the rnn.py script, and leave it running for between an hour and a week: it's training lots of models on the data in char-rnn/data/words. For each model, after a bit of training, the model will be run for a few hundred characters, so if you save the output of this script somewhere you can view the various model outputs later.

Now you'll need to look over the outputs of the models you've created and write some code to score the outputs of the models. Make sure to run the models at different temperatures, since some models run better at specific temperatures. Also make sure to run all trained epochs and not just the final epoch. Since there's so many of these tuples, it's helpful to write some code which will score the tuples for you automatically.

I made a bit of a mess in burgundy/rnn/explore.py, but the script contains all of the code I used to explore the outputs of the (model, epoch, temperature) tuples, so you can play around with that. Unfortunately it's too messy right now to just run without modifications.

After you've picked models which you like, you can use the burgundy/rnn/rnnserver.py script to keep a pool of words generated by those models and put them into a hosted queue. You can pull off the queue and host it on the web using burgundy/wordserver/wordserver.py. Make sure to ```pip install -r requirements.txt``` for the wordserver.
