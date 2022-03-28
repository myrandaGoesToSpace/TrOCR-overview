# TrOCR: Transformers-based Optical Character Recognition with Pre-Trained Models (2021)

## Overview
**What is Optical Character Recognition (OCR)?**
- Machine translation of images of text to machine-readable text
- Applications in record digitization and real-time translation
- Traditionally applied using a combined CNN and RNN model

**Problems with current methods**
- Very large models that must be trained from scratch
- No work using pre-trained models

### The Model: TrOCR
<img width="490" alt="model architecture of the TrOCR model" src="https://user-images.githubusercontent.com/36711263/160476700-dbd6e1e9-9b4b-4e3b-acf2-5c1811548f6c.png">
- resizes image to 384 x 384, then uses 16 x 16 segments as input to model

**Discussion Topic 1:** Do you think that this model is an encoder, decoder, or encoder-decoder, and why?

#### Initializing the Model
- Encoder: DeIT and BeIT (two image transformers) pretrained on ImageNet with Masked Image Modelling
- Decoder: RoBERTa
- Training data: 2 million pages from publicly available PDFs, SROIE (Scanned Receipts OCR and Information Extraction) dataset, and IAM Handwriting Dataset


**Discussion Topic 2:** What is the benefit of performing OCR in Transformers rather than CNN+RNN?

**Discussion Topic 3:** When describing the model pipeline, the paper says that, "During training, we rotate the sequence backward by one position and move the '[EOS]' token to the beginning," then feed this rotated sequence to the decoder, which generates output. What do they mean by "rotating" the text, and what purpose does this serve?
*This genuinely confused me, so please give me your thoughts!*

## Model Performance 
<img width="323" alt="trocr_eval" src="https://user-images.githubusercontent.com/36711263/160482541-bd221ae5-cba6-4946-8518-19edb63b2717.png">
Evaluation on the SROIE dataset

<img width="478" alt="trocr_cer" src="https://user-images.githubusercontent.com/36711263/160482574-a2f94d27-32d2-4d34-a320-81b0485b0aea.png">
Evaluation of Character Error Rate (CER) on the IAM handwriting dataset


## Resources
1. TrOCR: https://arxiv.org/pdf/2109.10282.pdf
2. TrOCR HuggingFace Space: https://huggingface.co/microsoft/trocr-base-printed
3. DeIT: https://arxiv.org/abs/2012.12877
4. BeIT: https://arxiv.org/abs/2106.08254
5. SROIE: https://paperswithcode.com/dataset/sroie
6. IAM Handwriting Dataset: https://paperswithcode.com/dataset/iam
