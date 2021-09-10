# NICE-Pretraining-Model---MAGIC
MAGIC model implementation will be coming soon....

MAGIC model is designed for the NICE-Setting II. It aims to generate emotional comments conditioned on an image, a comment topic, affect features, and the comment history. As large models usually generalize better to new domains when they are trained on large volumes of data, we use GPT-2 as the backbone for MAGIC. It is trained with the objective of predicting the next word, given an image, comment topic, comment history, affect feature, and all of the previous words within a defined context window. 
We trained MAGIC with the transformer architecture, which has 12 layers and each layer has 12 heads. The model aims to compute the conditional probability L:
L = P(C_k | I, H, A_k, C_1, ..., C_{k-1}), where C_k is kth comment in a image-comment thread, I is the image, H is the title of the thread, A_k is the affect feature of C_k, and
C_1, ..., C_{k-1} are previous comments.

When training MAGIC, we encode the input image I into a 2048-dimension feature vector using pre-trained Resnet-152 model. The affect and style features A_k are represented as a 64-dimensional affect feature vector. The encoded image feature vector, the affect feature vector, the embedded comment topic vector, the embedded history comments vectors and the embedded output comment vectors are concatenated together. The prediction loss is only computed for the current comment. 
