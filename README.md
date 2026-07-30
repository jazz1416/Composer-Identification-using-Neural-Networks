# Composer-Identification-using-Neural-Networks
**AAI511 - Neural Networks and Deep Learning**
**Final Team Project**

---

## Project Introduction
Our project objective was to build three different models in order to try to predict if a piece was created by Bach, Beethoven, Chopin, or Mozart based off of a musical score. We created a CNN model, a LSTM model, and a hybrid model to compare the results of each of these models.  

## Team
- Carlo Casella
- Jasmine Duong
- Emmanuel Sadek


## Table of Contents

1. [Dataset](#dataset)
2. [Project Structure](#project-structure)
3. [Technical Report Sections](#technical-report-sections)
4. [Model Selection](#model-selection)
5. [Results](#results)
6. [Technologies Used](#technologies-used)
7. [Challenges](#challenges)
8. [Contributions](#contributions)


## Dataset
**Source:** [midi_classic_music](https://www.kaggle.com/datasets/blanderbuss/midi-classic-music)

**Description:**

Our dataset is from Kaggle and contains 3929 midi files of classical works by 175 different composers. We filtered our data to only work with pieces composed by Bach, Beethoven, Chopin, and Mozart. 

---


## Project Structure
```
Composer-Identification-Using-Neural-Networks/
│
├── AAI-511_Final_Team_Project_Group_5_V1    # Initial attempt
├── AAI-511_Final_Team_Project_Group_5_V2   # Revised attempt
├── README.md                       # Project documentation
│
```

---

## Technical Report Sections

Our notebook follows the following structure:

### 1. **Dataset Filtering**
   - Load the dataset
   - Filter out only pieces from composers Bach, Beethoven, Choppin or Mozart

### 2. **Exploratory Data Analysis (EDA)**
   - Display the composer distribution
   - Pitch distribution
   - Note duration distribution
   - Tempo distribution
   - Sequence length distribution
   - Piano roll density distribution

### 3. **Windowing**
   - Create windows of size ___ and stride ___ for each composer

### 4. **Data Preprocessing**
   - Normalize data
   - Extract event sequences and pianoroll for neural networks
   - Extract music21 features

### 5. **Model Building and Training**
   - Early stopping and model checkpointing
   - Three different neural networks built through tensorflow
   - **CNN** — 2D CNN model with 3 layers and a classify and flatten layer using activation functions ReLu and Softmax
   - **LSTM** — 2 layer LSTM model with a fully connected classifier using activation functions ReLu and Softmax
   - **Hybrid** — Multi-layer CNN with LSTM layer

---

## Model Selection
Why each model picked, add later

## Results
add later

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
| `shutil` | File management and operations |
| `pretty_midi` | Midi file manipulation |
| `sklearn` | Model evaluation and data splitting |
| `tensorflow` | Model creation |

### Visualization
| Library | Purpose |
|---------|---------|
| `matplotlib` | Plotting and visualizations |

### Development Environment
- **Jupyter Notebook** — Interactive analysis and experimentation
- **Virtual Environment (venv)** — Dependency isolation

---
## Challenges
Our dataset was heavily in favor of Bach, our inital EDA showing there were 1049 Bach files, 213 Beethoven, 138 Chopin, and 259 Mozart. We also saw that the duration of the average duration of the Bach files was much shorter meaning if we set a static max note length when creating our models we would've run into issues regarding how much of a piece was looked at. To overcome this challenge, we created sliding windows to gather as much of each composers' piece for our model to learn off of at each iteration. 

Creating these windows was a challenge in it of itself. add later

## Contributions
- Carlo completed the initial data preprocessing and EDA. 
- Jasmine built and trained the models, helped revise the data preprocessing, managed the GitHub, completed the README. 
- Emmanuel completed the model evaluation and optimization, and created the windows for our data. 
