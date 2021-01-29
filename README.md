# Relation_Network
Implementation of Relation Network. Original paper: https://arxiv.org/abs/1706.01427

Implementation of Recurrent Relational Network. Original paper: https://arxiv.org/abs/1711.08028

This repository uses PyTorch v1.3 (Python3.7).

# Story Generate
This implementation tests the Relation Network model (RN) and the Recurrent Relational Network model (RRN) against the babi dataset, available at https://research.fb.com/downloads/babi/

# PRA
This repository uses Weights and Biases (W&B) to monitor experiments. You can create a free account on W&B (https://www.wandb.com/) or comment out the (few) lines starting with `wandb`. Without W&B, accuracy and loss plots will still be created and saved locally in the `results` folder.

# Train and Test RN
* Run `pip install -r requirements.txt`
* Create a folder `babi`
* Download the babi dataset (20 tasks) already divided and preprocessed in train, validation and test at this link: https://drive.google.com/drive/folders/1HkO_w7hbxxWZV4nbGl0Y2w_AuSa4ktub?usp=sharing and put the downloaded folder inside `babi`.
* Download the word dictionaries at: https://drive.google.com/drive/folders/1Ktd4kL1FJBiY_R_HoqlicjmRemkq8xzC?usp=sharing and put the downloaded folder inside `babi`.
* Create a folder `results` to store experiment results (both plots and saved models)
