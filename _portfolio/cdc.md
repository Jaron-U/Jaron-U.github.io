---
title: "Conditional Diffusion Compression"
excerpt: "compress image by using conditional diffusion model<br/><img src='/images/cdc.png'>"
collection: portfolio
---


A Reporece of the project "Conditional Diffusion Compression"
Github project Link: [https://github.com/Jaron-U/conditional_diffusion_compression](https://github.com/Jaron-U/conditional_diffusion_compression)

<img src='/images/cdc.png'>

## Introduction
This project is mainly divided into two parts: encoder and decoder.

* Encoder
The encoder primarily uses a VAE structure, which also consists of an encoder and decoder. The encoder downsamples the original image to map it to the latent space, then uses quantization compression, and finally uses the decoder to upsample and restore the image. 

* Decoder
The decoder is a DDPM model. It uses the output from the VAE as the condition for the diffusion model, and then restores the image again through a U-Net structure. The images restored through the diffusion model retain more details and have higher quality.

## Some changes
The method of reading the dataset has been modified. Instead of direct extraction, images are converted to a numpy structure during extraction and saved in h5 file format. This file format allows database-like access, reducing the number of files without affecting batch loading.

This is the ppt of the project: 
If the embedded PDF below does not load, you can <u><a href="https://jaron-u.github.io/files/cdc_presentation.pdf">download it here.</a></u> <br/> <embed src="https://jaron-u.github.io/files/cdc_presentation.pdf" type="application/pdf" width="100%" />