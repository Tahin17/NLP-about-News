CSE440 News Project

How to run:
1. Put the notebook/script in the same folder as:
   - Training_data_4.csv
   - Test_data.csv
2. Keep or create these folders in the same project directory if you want cached reruns:
   - processed_data
   - vectorizers
   - word2vec_models
   - checkpoints
   - histories
   - reports
   - plots
   - results
   - split_cache
3. Open a terminal in that project folder.
4. Run Jupyter from that folder and open the notebook.
5. Run all cells in order.

What this version changes:
- Reorganized to look more like Lab 1 to Lab 4
- Keeps only the required project items
- Saves preprocessing caches for raw, extreme, and optimum versions
- Saves experiment history, confusion matrices, classification reports, and neural histories
- Groups the sequence models by SimpleRNN, GRU, and LSTM families like the lab flow

Notes:
- The train/test split from the dataset is preserved.
- A validation split is created only from the training set.
- BERT is not included because it is optional in the project PDF.
- Neural models are implemented in PyTorch so CUDA can be used when available.
