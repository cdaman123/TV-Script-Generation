# TV-Script-Generation

In this project, I'll generate my own [Seinfeld](https://en.wikipedia.org/wiki/Seinfeld) TV scripts using RNNs.  I'll be using part of the [Seinfeld dataset](https://www.kaggle.com/thec03u5/seinfeld-chronicles#scripts.csv) of scripts from 9 seasons.  The Neural Network I'll build will generate a new ,"fake" TV script, based on patterns it recognizes in this training data.
```
Project Structure
 |
 +-- tv_script_generation.ipynb
 |  
 +-- helper.py
 |  
 +-- data
    |  
    \-- Seinfeld_Scripts.txt

```

We create a `helper.py` file which contain some functions which are used inside the project for example : 
* `load_data(path)`
* `preprocess_and_save_data(dataset_path, token_lookup, create_lookup_tables)`
* `load_preprocess()`
* `save_model(filename, decoder)`
* `load_model(filename)`

We can devide our Project in Some Steps which are given below:

* Step 1 : Get the Data  
* Step 2 : Explore the Data  
* Step 3 : Implement Pre-processing Functions  
* Step 4 : Check Point 1  
* Step 5 : Build the Neural Network  
* Step 6 : Neural Network Training  
* Step 7 : Checkpoint 2  
* Step 8 : Generate TV Script  

## Dataset Information

**Dataset Stats**
* Roughly the number of unique words: 46367
* Number of lines: 109233
* Average number of words in each line: 5.544240293684143

**The lines 0 to 10:**

*jerry: do you know what this is all about? do you know, why were here? to be out, this is out...and out is one of the single most enjoyable experiences of life. people...did you ever hear people talking about we should go out? this is what theyre talking about...this whole thing, were all out now, no one is home. not one person here is home, were all out! there are people trying to find us, they dont know where we are. (on an imaginary phone) did you ring?, i cant find him. where did he go? he didnt tell me where he was going. he must have gone out. you wanna go out you get ready, you pick out the clothes, right? you take the shower, you get all ready, get the cash, get your friends, the car, the spot, the reservation...then youre standing around, what do you do? you go we gotta be getting back. once youre out, you wanna get back! you wanna go to sleep, you wanna get up, you wanna go out again tomorrow, right? where ever you are in life, its my feeling, youve gotta go.*

*jerry: (pointing at georges shirt) see, to me, that button is in the worst possible spot. the second button literally makes or breaks the shirt, look at it. its too high! its in no-mans-land. you look like you live with your mother. *

*george: are you through? *

*jerry: you do of course try on, when you buy? *

*george: yes, it was purple, i liked it, i dont actually recall considering the buttons.*

## Neural Network 
We use `Adam Optimizer` and `Cross Entropy Loss` for train neural network and architecture of neural network as below :
```
RNN(
  (embedding): Embedding(21388, 150)
  (lstm): LSTM(150, 512, num_layers=2, batch_first=True, dropout=0.5)
  (fc): Linear(in_features=512, out_features=21388, bias=True)
)
```

## Hypermaters
We have 10 hyperparameters which are devided in 3 category.

### Data parameters
`sequence_length = 10`  
`batch_size = 128`  

### Training parameters
`num_epochs = 15`  
`learning_rate = 0.001`

### Model parameters
`vocab_size = len(vocab_to_int)`  
`output_size = vocab_size`  
`embedding_dim = 150`  
`hidden_dim = 512`  
`n_layers = 2`  
`show_every_n_batches = 500`  

## Generated Script

It's time to generate the text. Set `gen_length` to the length of TV script you want to generate and set `prime_word` to one of the following to start the prediction:
- "jerry"
- "elaine"
- "george"
- "kramer"

We can set the prime word to _any word_ in our dictionary, but it's best to start with a name for generating a TV script. (We can also start with any other names you find in the original text file!)

**Generated Script**

```
elaine: boutiques tragedy mentally annoying, and i think i have precedence control over the hall.

jerry:(shocked) i don't know..

jerry:(to the phone) yeah, it's unbelievable.

george:(to elaine, muffled) hey, hey. hey, hey.

jerry: hey, i got a little tied on the mollusk..

kramer: well, it's a puffy shirt.

kramer: hey, i saw the photo, but i think that i could talk to a friend of mine...

elaine:(interrupting) i don't have any money.

george:(to jerry) you wanna get that mail outta the way back, and i tripped...

jerry: i mean, you know i could've changed the whole thing.(to elaine) i mean.

george: i don't know...

jerry:(to george, whispering) hey, you know, lloyd advises dinkins have left me a lot of people.

elaine: well, you know what? i think i may.

jerry: well, i think it would be nice if you can get a pedicure immediately and do you know how i feel about that?

kramer: oh, yeah...

george: you know what, i could do a little snooping skits.(george looks shocked and sees jerry staring at the prospect)

jerry:(pointing) i can't take you any fresher, you can't get out of here.

jerry:(pleading) you know, the whole block is based on your head.

kramer: well, you know, i think you should call him.

elaine: what?

george: well, you know... i was thinking maybe i could have been able to buy him a brand- bedroom suite.

george: what, you don't think you could do something about it.

george: oh, i don't think so.

elaine:(to kramer) so how was it?
```
