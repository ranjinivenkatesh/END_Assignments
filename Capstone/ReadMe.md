Capstone
Objective and Guidelines
The capstone project is to write a transformer-based model that can write python code (with proper white-space indentations). Here are the key points:

The dataset can be found here. The dataset has 4600+ examples of English text to Python code.
Write a transformer-based model that can learn to translate English to Python.
Must use transformers with self-attention, multi-head, and scaled-dot product attention in the model
There is no limit on the number of training epochs or total number of parameters in the model
Train a separate embedding layer for python keywords that pays special attention to whitespaces, colon and other things (like comma etc)
Your model has failed the capstone score if:
your model fails to do proper indentation
your model fails to use newline properly
your model has failed to understand how to use colon (:)
your model has failed to generate proper python code that can run on a Python interpreter and produce proper results
You need to take care of some preprocessing things like:
the dataset provided is divided into English and "python-code" pairs properly
the dataset does not have anomalies w.r.t. indentations (like a mixed-use of tabs and spaces, or use of either 4 or 3 spaces, it should be 4 spaces only). Either use tabs only or 4 spaces only, not both
the length of the "python-code" generated is not out of your model's capacity
You need to submit a detailed README file that:
describes the data clean required
your model architecture and salient features w.r.t. the model we wrote in the class
describes the loss function and how is it unique or improved than just using cross-entropy
your data preparation strategy
your data extension strategy (if you add more data)
your "python-code" embedding strategy
your evaluation metrics
25 example output from your model
attention graph/images between text and "python-code"
any additional point you'd want to add
The project mainly having the following components:

Data Pre-processing
Embedding Creation
Sequence to Sequence Model Building
Training
Inference
** Data Pre-processing: **

The important step in building the complete solution for generating the python source code is pre-processing the given dataset. The dataset has Program Description consisting of numbers, special symbols and extra spaces. The Program code also having comment lines for some parts of the code, which is causing ambiguous when splitting the data with Special character '#', so the comment lines across all the programs are removed to resolve the ambiguity.

Program text and Program code has some additional new lines and empty lines in between, removing them also considered in pre-processing step.

** Embedding Creation: ** Embedding is the process of representing a word or text in vector or number format with specific dimension.

As, the python code consisting on various special characters, generating embedding for each character will improve the model performance, than assigning a random values.

For generating embedding for Python code, gensim with Word2Vec model has be utilized and created a embedding with the same dimension ie 256.

Sequence to Sequence Model Building

The model built for achieving the desired result with the reference of Attention is all you need, a transformer model by Google in 2017.

The transformer model consists of Encoder and Decoder block with varying number of blocks in each part. Here we experimented with various number of blocks in Encoder and Decoder also. Finally we used Three Encoder blocks and 3 Decode blocks.

Each Encoder block consisting of same architecture as Attention All you need paper with Mutli-head Attention and FUlly Connected Network Each Decode block also having similar structure with Masked Attention, Mutli-head Attention and fully connected network.

Training: The Complete sequence to Sequence model created and Trained for 50 Epochs.

Inference To check the performance and Validate, the inference part created with a single Natural Language Statement, for which the python source need to be generated.
