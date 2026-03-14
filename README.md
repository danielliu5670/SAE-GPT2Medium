---
license: cc-by-sa-4.0
language:
- en
tags:
- code
size_categories:
- 1M<n<10M
---

# Putting Words in GPT-2's Mouth with Sparse Autoencoders!

<img src="https://cdn-uploads.huggingface.co/production/uploads/697ea7ec19a454fc10134d9e/_vBn22qG1u_VH5SJbiZFa.png" width="350">

This is the HuggingFace dataset repository accompanying my project, which showcases the training and use of a primitive sparse autoencoder on GPT-2 Medium. Inside, I include an example of how my sparse autoencoder can be used to influence the model's output, as well as a sandbox that you can use to customize boosting a feature of your choice. The link to the Colab Notebook for the project can either be found in the home directory of this repository, or at [this link](https://colab.research.google.com/drive/1c9WO334hTxeOLMADksy1rbtoTlp_we72?usp=sharing).

*Very Important Note: Some of the most important files are too large to be stored on GitHub. They are, instead, hosted on HuggingFace, which you can find [here](https://huggingface.co/datasets/danielliu1/SAE-GPT2Medium).*

*Also Important Note: Make sure you create a copy of the Colab Notebook in your Drive - otherwise, you won't be able to save your changes.*

Inside this repository are all the files you will need to run the necessary components of the Notebook. 

## Dataset Info

For those who are interested in reappropriating this data for their own purposes, feel free! Below is a description of each of the files:

1. `activations.npy` (`2264880, 1024`): contains the raw and unnormalized activations that were extracted from the 20th layer of GPT-2 Medium, using the WikiText-2 training dataset. **This is one of the files being stored on HuggingFace.**
2. `activations.pt` (`2264880, 1024`): contains the same activations, but normalized to a mean of 0 and variance of 1. It's also in the form of a tensor. **This is one of the files being stored on HuggingFace.**
3. `activations_mean.pt` (`scalar`): contains the mean of the data from `activations.npy`.
4. `activations_std.pt` (`scalar`): contains the standard deviation of the data from `activations.npy`.
5. `enc_weights_fnl.pt` (`1024, 4096`): contains the (trained) encoder weight matrix.
6. `enc_bias_fnl.pt` (`4096,`): contains the (trained) encoder bias vector.
7. `dec_weights_fnl.pt` (`4096, 1024`): contains the (trained) decoder weight matrix.
8. `dec_bias_fnl.pt` (`1024,`): contains the (trained) decoder bias vector.
9. `wikitext_act.pt` (`82764, 4096`): contains the activations extracted from the hidden layer of the trained sparse autoencoder (after passing through GPT-2 Medium), using the first 500 entries of the WikiText-2 training dataset. **This is one of the files being stored on HuggingFace.**
10. `wikitext_tk.pt` (`82764`): contains an ordered vector of every decoded token, each of which corresponds to a row of activations from `wikitext_act.pt`.

## SAE Specifications

The sparse autoencoder itself was trained with a factor of 4 (which produced a 4,096-dimensional hidden layer). It achieved an MSE of 0.071 (which is approximately 93% of the variance explained, using my normalized activations) and an L0 sparsity of 79.62.

## Contact

For any complaints or comments about either this dataset repository or the Colab Notebook, please send me an email at danielliu.datascience@gmail.com. Thank you very much! Have fun!
