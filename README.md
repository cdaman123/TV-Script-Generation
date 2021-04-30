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
