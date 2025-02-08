### **Task Description**  

Playlist recommendation is a task in recommender systems that aims to suggest songs to complete a
partial playlist. Given a set of playlists and their associated tracks, the goal is to predict 
which songs a user would add to an incomplete playlist based on historical data.  

#### **Examples:**  
- **Input (Partial Playlist):** `[Imagine (John Lennon), Let it Be (The Beatles)]`  
  - **Expected Output:** `[Blackbird (The Beatles), Hallelujah (Jeff Buckley)]`  

- **Input (Partial Playlist):** `[Stronger (Kanye West), Eye of the Tiger (Survivor)]`  
  - **Expected Output:** `[Lose Yourself (Eminem), Can’t Hold Us (Macklemore)]`  

---

### **Dataset**  

A commonly used dataset for playlist recommendation is the **Million Playlist Dataset (MPD)**
from Spotify. This dataset contains **1,000,000 user-generated playlists**, with information such as:  

- **Playlist Title**  
- **Included Tracks** (artist, title, unique ID)  
- **Number of Tracks per Playlist**  
- **Associated User** (anonymized)  

📥 **Download:** [Spotify Million Playlist Dataset](https://www.kaggle.com/datasets/himanshuwagh/spotify-million?resource=download)
*(Requires a free Kaggle account).*  

Once downloaded, it is recommended to save it in a **Google Drive directory** and use `gdown` 
to download it for further processing.  

---

### Evaluation Metrics

- **Precision@k**: The percentage of suggested tracks that actually belong to the real playlist.

  Precision@k = (Number of correct tracks in the top k positions) / k

- **Recall@k**: The percentage of real tracks that have been retrieved among the suggested ones.

  Recall@k = (Number of correct tracks retrieved) / (Total number of real tracks)

- **Mean Reciprocal Rank (MRR)**: The reciprocal of the position of the first correct track in the recommendations.

  MRR = 1 / (Position of the first correct track)
 
---

### **Project Progress & Implemented Features**  

This project explores two different methods for playlist recommendation: 
- **Matrix Factorization** including Non-negative Matrix Factorization and Singular Value Decomposition
- **Language Model Approach** treating playlist recommendation as a sequence prediction problem.
Below is a summary of what has been done:  

#### ✅ **Dataset Exploration & Preprocessing**  
- Extracted some information on the data distribution once loaded the **Million Playlist Dataset (MPD)** from Kaggle.  
- Filtered out duplicate or irrelevant data to improve recommendation quality and optimize RAM usage.  

#### ✅ **Matrix Factorization Approach**
- **Sparse Matrix Representation**: Constructed a playlist-track interaction matrix, treating playlists
  as users and tracks as items.
- Implemented **Non-negative Matrix Factorization (NMF)** and **Singular Value Decomposition (SVD)**.  
- Optimized models using hyperparameter tuning.  
- Evaluated performance using **Precision@k, Recall@k, and MRR**.
- **Performance Comparison**: Analyzed accuracy vs. computational efficiency between NMF and SVD models.

#### ✅ **Language Model Approach**  
- **Streaming-Based Data Loading**: Implemented a data generator to process playlists on-the-fly, reducing memory usage.
- **Vocabulary & Tokenization**: Constructed a track vocabulary, mapping each song to a unique token for model input.
- **Custom PlaylistModel Architecture**: Designed a deep learning model using embedding and linear layers and batch normalization to capture playlist structures.
- **Efficient Training & Optimization**: Used Cross-Entropy Loss, SGD optimizer, and other tecniques to increase speedup and prevent overflow.
- **Evaluation & Metrics**: Assessed performance using Precision@k, Recall@k, and MRR.
