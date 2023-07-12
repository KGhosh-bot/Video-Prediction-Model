# Next Frame Prediction
Predicting the next frame in a short movie sequence
This project uses the Moving MNIST dataset, composed of 10,000 video sequences, each consisting of 20 frames. In each video sequence, two digits move independently around the frame, which has a spatial resolution of 64×64 pixels. The digits frequently intersect with each other and bounce off the edges of the frame.

While each sequence has a lenght of 20, I use **only 3 consecutive frames as input**, and **predict the next one**.

The model, a personalized verson of SimVP, consists of an encoder, a
translator and a decoder built on CNN only.
1. The encoder is used to extract spatial features,
2. the translator learns temporal evolution, and
3. the decoder integrates spatio-temporal information to predict future frame.

The model is based on this structure.

![model_structure](https://github.com/KGhosh-bot/Next_frame_prediction/assets/76099938/ff8723c2-c837-4543-9afb-29c7c0f8d2c5)

where in this case the number of channels C for Moving MNIST is 1 (single channel for grayscale).
The input/output shape is (H, W, T) for Height, Width and Frames

Input is $x[0 : (n-1)]$

Output is $x[n]$

where n is number of frames

![Detailed structure](https://github.com/KGhosh-bot/Next_frame_prediction/assets/76099938/c6e7a186-020b-4feb-99aa-9a5cff03f501)

The Inception Module used here is a generic Inception module with dimention reduction.

kernel sizes [1,3,5,7]

Library - Keras
