---
author: Demi_YuHongJun
comments: true
date: 2023-03-30 05:42:32+00:00
layout: post
title: How to Run Your Own LLaMA
description: How to Run Your Own LLaMA
keywords: LLaMA OpenAi
categories:
- frontend
- javascript
tags:
- javascript
---
* 目录
{:toc}
---

How to Run Your Own LLaMA

LLaMA model weights are available over the internet on various websites. This is not legal but I am sharing just a “How to — tutorial”

All work shown here is provided by LLaMAnnon

Download LLaMA Weights
magnet:xt=urn:btih:b8287ebfa04f879b048d4d4404108cf3e8014352&dn=LLaMA&tr=udp%3a%2f%2ftracker.opentrackr.org%3a1337%2fannounce
Get the .torrent file here.

Please download and seed all the model weights if you can. If you want to run a single model, don’t forget to download the tokenizer.model file too.

Set up Conda and create an environment for LLaMA
The official method recommended by meta is using Conda so -

### Set up Conda

1. Open a terminal and run: wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
2. Run chmod +x Miniconda3-latest-Linux-x86_64.sh
3. Run ./Miniconda3-latest-Linux-x86_64.sh
4. Go with the default options. When it shows you the license, hit q to continue the installation.
5. Refresh your shell by logging out and logging in back again.

### Create env and install dependencies
```
Create an env: conda create -n llama
Activate the env: conda activate llama
Install the dependencies:
NVIDIA:
conda install torchvision torchaudio pytorch-cuda=11.7 git -c pytorch -c nvidia
AMD:
pip3 install torch torchvision torchaudio --extra-index-url https://download.pytorch.org/whl/rocm5.2
Clone the INT8 repo by the user tloen: git clone https://github.com/tloen/llama-int8 && cd llama-int8
Install the requirements: pip install -r requirements.txt pip install -e .
```
### Create a swapfile

Loading the weights for 13B and higher models need a considerable amount of DRAM. IIRC it takes about 50GB for 13B, and over 100GB for 30B. You’ll need a swap file to take care of excess memory usage. This is only used for the loading process; the inference is unaffected (as long as you meet the VRAM requirements).

```
Create a swapfile: sudo dd if=/dev/zero of=/swapfile bs=4M count=13000 status=progress This will create about ~50GB swapfile. Edit the count to your preference. 13000 means 4MBx13000.
Mark it as swap: sudo mkswap /swapfile
Activate it: sudo swapon /swapfile
```

If you want to delete it, simply run sudo swapoff /swapfile and then rm /swapfile.

### Run the models
I’ll assume your LLaMA models are in ~/Downloads/LLaMA.
```
Open a terminal in your llama-int8 folder (the one you cloned).
Run: python example.py --ckpt_dir ~/Downloads/LLaMA/7B --tokenizer_path ~/Downloads/LLaMA/tokenizer.model --max_batch_size=1
You’re done. Wait for the model to finish loading and it’ll generate a prompt.
```
### Add custom prompts
By default, the llama-int8 repo has a short prompt baked into example.py.
```
Open the example.py file in the llama-int8 directory.
Navigate to line 136. It starts with triple quotations, """.
Replace the current prompt with whatever you have in mind.
```
Good luck!! The word on the street is that the 7b model is pretty dumb and that's the only version fitting on an enthusiast GPU (16-24gb; 8gb is a NO-GO). There are some tricks to fit a 13B model to fit (using 8bit memory shenanigans but I have not done that and I am not sure how it affects the model itself).

If you have read it until this point — Thank you! You are a hero! To support me
