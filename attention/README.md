# [coursera course](https://www.coursera.org/learn/advanced-deep-learning-methods-healthcare/supplement/nv3kH/about-this-course)

# Notes
* [Attention](https://d3c33hcgiwev3.cloudfront.net/Z3RtP0aCS0K0bT9GgstCNg_2add63ccd02d4fdcaf7c65b1c7526f9b_lec9-Attention.pdf?Expires=1724457600&Signature=FQj50kMWx6r93lh5vB9fNtFNDbcBQs-6PhZUdjn2q~OdBJRDHHMm2V1REURv1GiSK8swMSAceT-C5drDEYxWk6DtDFkOcnKVghj10zkjlvAgXut73aBwecH3h1TJUiqT3bGTd6asJ~WefaQQ1Bcs8UPFC2ou0zoALIyS2r4QKpo_&Key-Pair-Id=APKAJLTNE6QMUY6HBC5A)
    * ![image](https://github.com/user-attachments/assets/d4cdb50e-d8d5-4a17-a7e1-e21ef7bfa508)
* [Graph Neural Networks](https://d3c33hcgiwev3.cloudfront.net/ACENZeIfTVahDWXiH31W_g_3ab6e811d62c4790841800b82cc8c3ce_lec10_GNN.pdf?Expires=1724457600&Signature=kMR1FWHESLKpAfKh141pYR1HGDXHw3w4nG4FYEVeIMQ9~biwBgY9Mob0qcvfJ1IHy8utRB3jHHObTHjkrr1vlaWZuy-dcSYnfxQ1R00mZhWJ6vKg4kLVCMJsBhYvF6Dn7G9WB4LLVP8UTlw4zIUOARwyzYoAQaEsq148ne8vrp0_&Key-Pair-Id=APKAJLTNE6QMUY6HBC5A)
    * node embedding: map nodes to d-dimensional vectors such that similar nodes are close to each other
    * Graph convolutional networks (GCN)
    * Message passing neural network (MPNN)
    * Graph attention networks (GAT): combine attention with CNN
* [Memory networks](https://d3c33hcgiwev3.cloudfront.net/g9POF4pUR4uTzheKVEeLMw_8b70f6ca6d4944abad7858e59ccc6be5_lec11-memory-network.pdf?Expires=1724457600&Signature=I0L50yZCXeWJRumYCbddiTS4FXiS9ExOA56ewwuioRZ2-fwlfIqFvcKefH9xGYmWCOIDW3Vic5DSEPCK4anGxgcnzFXrbgHH~rQimxbJ8wLxBuezT6UjBdZzrKAGFsa2p8cCKvP5YRLRETO5b4RRyLxlNp19Qqc5-KfINp7KVs4_&Key-Pair-Id=APKAJLTNE6QMUY6HBC5A)
   *  the original memory network uses this external memory component to assist deep neural network. The idea is to try to remembering and storing information that can be useful.
      *  ![image](https://github.com/user-attachments/assets/0c919a44-679f-4700-93e7-b192e70e1ded)
      *  I: input feature map,
         *  convert input x to an internal feature representation,
         *  options: simple bag of words - one hot encoding / RNN if the input are sequencs
      *  G: generalization:
         * updates old memories given new input x
         * mi = G(mi, I(x), m) for all i. for each memory slot, try to get function G with I(x) and entire m
         * simplest version is to store I(x) in a slot of memory, mH(x) = I(x) where H(x) is the has function for finding the memory location to store 
      *  O: output feature map
         * ![image](https://github.com/user-attachments/assets/08a0e549-64be-4db6-ba07-189561f11f7c)
      *  R: response
         * map output to the final  response r=R(o)
         * e.g. softmax for classification, RNN for sequence generation
   * End-to-end memory network: replace the argmax with softmax with attention
      * ![image](https://github.com/user-attachments/assets/0876df10-d13d-45e9-83e7-4366c9d73482)
      * key ideas: use softmax attention to replace argmax operation / use question answer template to model memory network / allow end-to-end training
* transformer
   * transformer is an effective embedding method for sequential data using self-attention strategy, to make seq2seq model with attention train faster 
   * ![image](https://github.com/user-attachments/assets/0ef626aa-de71-48d8-87e8-aa37a4d42460)
   * Encoder
      * Three verrsion of embedding can be trained in parallel: Q: query, K: key, V: value  
         * ![image](https://github.com/user-attachments/assets/6afd8880-f988-40f4-b586-17f3988d6bc3)
      * multi-head attention: repeat the same attention procedure multiple times with different initialization
      * position-encoding: add some position specific information to the input
   * Decoder
      * output embeddings of encoder become the input to decoder
      * self-attention with future mask
         * ![image](https://github.com/user-attachments/assets/69741ba7-08ea-45fc-b3c2-c20a3e661203)
      * encoder-decoder attention
         *  keys K and values V from the encoder are reused in encoder-decoder attention
      * ![image](https://github.com/user-attachments/assets/e3621b3b-5c80-4b3e-9120-1f548957dbd5)
   * BERT
      * context specific embedding: BERT computes dynamic embedding for each word (word2vec is static embedding for each word)
      * masked language model: BERT masks x% input words, and try to predict what they are (existing deep learning model: RNN or bidirectional RNN, from left to right or right to left) 
 
* [Deep Generative Models](https://d3c33hcgiwev3.cloudfront.net/aD-03HDNSfm_tNxwzYn5Jg_3889af6b109d41b680d9c610cfa7f7d2_lec12-generative-models.pdf?Expires=1724457600&Signature=ZYQ95JoJ1qaT~biwJgAcvFafgyfYnbaN-LMiDCN7MvupLzwjW1Qs-gf-EZnvVfJX6WepSKQ-8YiNY5rJyTR2bUMIFQ8l2sm2FxXp63bu4B2SWPC892nnOuq7dZv97gfZknQplcWzbLzxMphWffFvZqMpC2AZJgpdpgFYoIB3ZoI_&Key-Pair-Id=APKAJLTNE6QMUY6HBC5A)

# Assignment: 
https://github.com/dennislamcv1/UoIDLHealthcare/tree/main 
