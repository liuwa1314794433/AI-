# Tutorial-machine translation

## The Problem: Chinese-English translation

   In this tutorial, we'll build a simple Chinese-English translation model.

## Seq2Seq model
   A simple Seq2Seq model consists of three parts, Encoder-LSTM, Decoder-LSTM, and Context.The input sequence is ABC, and Encoder-LSTM processes the input sequence and returns the hidden state of the entire input sequence in the last neuron, also known as the context (C).Decoder-LSTM then predicts the next character of the target sequence step by step based on the hidden state.The final output sequence wxyz.It is worth mentioning that the author Sutskever designed a specific Seq2Seq model based on his specific tasks.The input sequence is processed in reverse order, which enables the model to process long sentences and improves the accuracy.  

## 1. Data preprocessing
- Dataset  
    The language translation model that we are going to develop will translate English sentences into their Chinese language counterparts. To develop such a model, we need a dataset that contains English sentences and their Chinese translations. This dataset is from http://www.manythings.org/anki/.  

- Data Preprocessing
    In our dataset, we do not need to process the input, however, we need to generate two copies of the translated sentence: one with the start-of-sentence token and the other with the end-of-sentence token.  

    start-of-sentence token: '\t'  
    end-of-sentence token: '\n'  


## 2. Word embedding and padding
   Map data sample according to dictionary index.  

   - en_num_data - encoder input data
   - ch_num_data - decoder input data (with sos)
   - de_num_data - decoder target output data (with eos)

## 3. Create the Model
- Encoder
  The input to the encoder will be the sentence in English and the output will be the hidden state and cell state of the LSTM.  
  
- Decoder
  The decoder will have two inputs: the hidden state and cell state from the encoder and the input sentence, which actually will be the output sentence with an token appended at the beginning.  

## 4. Train the model

## 5. Modifying the Model for Predictions
   While training, we know the actual inputs to the decoder for all the output words in the sequence. The input to the decoder and output from the decoder is known and the model is trained on the basis of these inputs and outputs.  

   However, during predictions the next word will be predicted on the basis of the previous word, which in turn is also predicted in the previous time-step. Now you will understand the purpose of sos and  eos tokens. While making actual predictions, the full output sequence is not available, in fact that is what we have to predict. During prediction the only word available to us is sos since all the output sentences start with sos.  

## 6. Make predictions
- In this step, you will see how to make predictions using English sentences as inputs.

- We pass the test input sequence to the encoder_model, which predicts the hidden state h and the cell state c.

- Next, we define a variable target_seq, which is a 1 * 1 matrix of all zeros. The target_seq variable contains the first word to the decoder model, which is sos.

- In the next line, the outputs list is defined, which will contain the predicted translation.

- Next, we execute a while loop.

    Inside the loop, in the first iteration, the decoder_model predicts the output and the hidden and cell states, using the hidden and cell state of the encoder, and the input token, i.e. sos. The index of the predicted word is stored in sampled_token_index. The predicted index is then appended to the outputs list. The index of the predicted word is stored in the target_seq variable. In the next loop cycle, the updated hidden and cell states, along with the index of the previously predicted word, are used to make new predictions. The loop continues until the maximum output sequence length is achieved or the eos token is encountered.
