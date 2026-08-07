# Composer-Identification-using-Neural-Networks
**AAI511 - Neural Networks and Deep Learning**
**Final Team Project**


---


## Project Introduction
Our project objective was to build two different models in order to try to predict if a piece was created by Bach, Beethoven, Chopin, or Mozart based off of a musical score. We created a CNN model and a LSTM model to compare the results of each of these models.  


## Team
- Carlo Casella
- Jasmine Duong
- Emmanuel Sadek




## Table of Contents


1. [Dataset](#dataset)
2. [Project Structure](#project-structure)
3. [Technical Report Sections](#technical-report-sections)
4. [Results](#results)
5. [Technologies Used](#technologies-used)
6. [Challenges](#challenges)
7. [Contributions](#contributions)




## Dataset
**Source:** [midi_classic_music](https://www.kaggle.com/datasets/blanderbuss/midi-classic-music)


**Description:**


Our dataset is from Kaggle and contains 3929 midi files of classical works by 175 different composers. We filtered our data to only work with pieces composed by Bach, Beethoven, Chopin, and Mozart. 


---




## Project Structure
```
Composer-Identification-Using-Neural-Networks/
│
├── AAI-511_Final_Team_Project_Group_5  # Complete notebook
├── README.md                       # Project documentation
│
```


---


## Technical Report Sections


Our notebook follows the following structure:


### 1. **Data Collection**
   - Download the dataset

### 2. **Data Preprocessing and EDA**
   - Extract notes from MIDI files
   - Create hash values for each file
   - Exploratory data analysis
   - Remove duplicate MIDI files
   - Invoke restrictions on files for number of instruments and duration

### 3. **Feature Engineering**
   - Convert each piece's notes into a DataFrame
   - Add calculated features such as rolling pitch statistic and note count

### 4. **Song Snipped Window**
   - Create 30 second windows with 20 second strides across every piece
   - Store each snippet with its composer and song name

### 5. **Split Data**
   - Collects unique songs
   - Stratified 70/15/15 split for training, test, and validation splits
   - Balance dataset
   - Scale features

### 6. **Model Building**
   - Early stopping and reduce learning rate on plateau
   - Two different neural networks built through tensorflow
   - **LSTM** — Bidirectional LSTM model with 2 layers, self attention, global max pooling, softmax output layer
   - **CNN** — 1D CNN model with 3 layers, global max pooling, ReLU and softmax activation functions
   - Training and evaluations for each model

### 7. **Hyperparameter Tuning**
   - LSTM hyperparameter tuning using `keras_tuner`, choices for LSTM units, dropout values, activation functions, dense neuron values, learning rate
   - CNN hyperparameter tuning using `keras_tuner`, choices for convolutional layer values, number of convolution blocks, dropout layer values, activation functions, number of dense layers, learning rate
   - Training of new model
   - Comparison with untuned model


---


## Results
$\quad$ The results of this project are two sets of neural network models, trained to predict a composer from a list composed of Bach, Mozart, Chopin, or Beethoven, based on sheet music. The two sets of models are composed of one trained and one untrained version of either a CNN or LSTM model.




$\quad$ Through hyperparameter tuning using a Keras built in tuner, we were able to slightly improve the performance of both models. The LSTM hyperparameter tuning involved trying different units for the LSTM units, dropout values, activation function choices, dense neuron values, and learning rate. Each of these values were chosen from a list of possible options that the tuner was to filter through and determine which values created the highest accuracy. As a result, some evaluation metrics decreased, while others increased, but the overall accuracy slightly increased. For the different composers, Mozart had a slight drop in recall, but saw improvement in recall and f1, while Chopin and Bach saw an increase in both. Beethoven had mixed results, as the recall slightly decreased, but the precision slightly increased. The overall accuracy for each model went from 0.639 to 0.691, however, indicating that the model performance very slightly increased. 




$\quad$ The CNN model was harder to tune. We tuned factors such as the initial convolution filter value, the number of convolution blocks, the activation function used, the dropout value, the number of dense layers, dense neuron values, and the learning rate. As a result, the overall accuracy also slightly increased from 0.657 to 0.671. Compared to the untuned version, most precision and recall values increased aside from Beethoven's precision slightly decreased as well as Mozart and Chopin's recall scores.


---


## Technologies Used


### Programming Language
- **Python 3.13**


### Core Libraries
| Library | Purpose |
|---------|---------|
| `pandas` | Data manipulation and analysis |
| `numpy` | Numerical computing |
| `os` | Operating system interactions |
| `pretty_midi` | Midi file manipulation |
| `sklearn` | Model evaluation and data splitting |
| `tensorflow` | Model creation |
| `keras_tuner` | Model tuning |


### Visualization
| Library | Purpose |
|---------|---------|
| `matplotlib` | Plotting and visualizations |


### Development Environment
- **Jupyter Notebook** — Interactive analysis and experimentation
- **Virtual Environment (venv)** — Dependency isolation


---
## Challenges
Our dataset was heavily in favor of Bach, our initial EDA showing there were 1049 Bach files, 213 Beethoven, 138 Chopin, and 259 Mozart. We also saw that the duration of the average duration of the Bach files was much shorter meaning if we set a static max note length when creating our models we would've run into issues regarding how much of a piece was looked at. To overcome this challenge, we created sliding windows to gather as much of each composers' piece for our model to learn off of at each iteration. 


## Contributions
- Carlo completed the initial data preprocessing and EDA. 
- Jasmine built and trained the initial models, helped revise the data preprocessing, completed the hyperparameter tuning and conclusion, managed the GitHub, and completed the README. 
- Emmanuel revised the data preprocessing and EDA, built and trained our current CNN and LSTM models, and completed evaluations for both. 






