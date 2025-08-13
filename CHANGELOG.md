# Changelog

Since the creation of this repository, the world of AI has been evolving at full speed. As such, this repository has been continually updated and upgraded.
The updates were made continually, so starting October 30, 2024, I began to note all the changes in this document.

This changelog contains the notable updates to the Transformers for NLP and Computer Vision 3rd Edition repository to adapt to the 
fast-evolving Generative AI market.

## August 14, 2025

`Chapter08/Fine_tuning_GPT_4.1_mini_SQuAd.ipynb` has been added to replace the existing fine-tuning notebooks, which contain models that are no longer supported by OpenAI.

A fallback has been added to run the fine-tuned model once the job is finished:
 `model=first_non_empty_model or "gpt-4.1-mini-2025-04-14"`

That way, if the job is not finished yet, the rest of the code will still respond to prompts.

# May 6, 2025

`DeepSeek_attention_head_RoPE.ipynb` in Chapter02

In a standard Transformer, position vectors (e.g., sinusoidal or learned) are added to token embeddings at the bottom of the model. This means that attention heads see only the sum.
DeepSeek-V3’s Multi-Head Latent Attention (MLA) instead interleaves position rotations after projecting into key/query subspaces.

## May 5, 2025

`DeepSeek_R1_Zero_RL.ipynb` in Chapter02

Traditional pipelines stack pre-training → supervised fine-tuning → reinforcement learning. DeepSeek-R1-Zero throws out that middle step—we apply pure RL directly on a base model, using simple, rule-based rewards to sculpt reasoning abilities from day one. This isn’t incremental—it’s a leap.

## April 29, 2025

`Google_Gemini_2.5_Flash.ipynb` in Chapter14
The notebook contains a wide variety of generative AI tasks applied to `Gemini 2.5 Flash`.

🎇Scientific Analysis & Reasoning: Demonstrated the ability to analyze complex scientific topics, such as the implications of exoplanets...
🎇Philosophical Inquiry: Explored abstract concepts like 'absurdity' in existentialism, discussing its relationship with the human search...
🎇Creative Writing: Generated a short story based on a creative prompt about a mysterious key, showcasing its imaginative and narrative abilities.
🎇Technical Problem Solving: Described a comprehensive approach to diagnosing and mitigating intermittent failures...
🎇Ethical Dilemma Analysis: Discussed the ethical considerations in the autonomous vehicle "trolley problem," ...
🎇Legal Analysis: Analyzed the legal implications of facial recognition technology, balancing security concerns and privacy rights...
🎇Economic Forecasting: Evaluated the potential impact of a global recession on emerging markets,...
🎇Medical Case Study: Formulated a differential diagnosis and diagnostic workup for a patient presenting with complex symptoms. 
🎇Coding Challenge: Developed a Python function for a binary search algorithm, demonstrating code generation and explanation capabilities.
🎇Social Commentary: Analyzed the impact of social media on political...
🎇Environmental Analysis
🎇 Linguistic Exploration
🎇Mathematical Problem: Described the Riemann hypothesis and its significance, explaining the implications of its truth or falsity. 
🎇Psychological Analysis: Discussed cognitive dissonance...
🎇Sociological Inquiry: Analyzed social mobility in modern societies, examining contributing factors and impact on inequality. 
🎇Literary Critique: Provided a critical analysis of Mary Shelley's Frankenstein...
🎇Artistic Interpretation: Interpreted Van Gogh's The Starry Night...
🎇Music Analysis: Analyzed Beethoven's...
🎇Film Studies: Examined the evolution of film as an art form...
🎇Computer Vision: The notebook also included a section demonstrating Gemini's multi-modal capabilities by analyzing an image of Salvador Dalí's...



## March 12,2025

Chapter06.KantaiBERT.ipynb
Hugging Face transformers require an accelerator which in turn requires a GPU. 
The latest version of Transformers installed right now in the notebook has dependency conflicts.

Use with(October 2024) versions of Transformers of Accelerate
pip install Transformers==4.46.1
pip install accelerate==1.0.1

## February 12, 2025
A notebook showing the reasoning capacity of OpenAI o3 in Chapter 7:    
`OpenAI_Reasoning_models_o3_API.ipynb`    
Model implemented **o3-mini**    

Upgraded *o1-preview to o1* in the `OpenAI_Reasoning_models_o3_API.ipynb` notebook (Chapter 7)   

## January 29, 2025
A notebook showing the reasoning capacity of DeepSeek has been deployed in the Chapter01 directory in the following section of Chapter 1:
**DeepSeek Reasoning models with DeepSeek R1, HuggingFace, and Together**
Model implemented: **deepseek-ai/DeepSeek-R1**
It demonstrates the self-reflecting ability of DeepSeek.

## January 25, 2025
Chapter 8: Fine-tuning OpenAI Models shows how to fine-tune a model.
Advanced RAG technology can be an alternative. As such a section was added to Chapter 8:
🐬RAG as an alternative to fine-tuning: Building Scalable Knowledge Graph-based RAG with Wikipedia and LlamaIndex	
This leads to an open-source package of three notebooks.

## January 12, 2025

Comments updated in `Chapter16/Open AI Vision with GPT-4o` 

**Before October 30, 2024, the repository was also continually updated.** You can rely on the icons in front of the notebooks in the [README  file](https://github.com/Denis2054/Transformers-for-NLP-and-Computer-Vision-3rd-Edition/blob/main/README.md) to find the evolutions:  
Look for 🐬 to explore *new bonus notebooks* such as OpenAI o1's reasoning models, Midjourney's API, Google Vertex AI Gemini's API, OpenAI asynchronous batch API calls!           
Look for 🎏 to explore existing notebooks for the *latest model or platform releases*, such as OpenAI's latest GPT-4o and GPT-4o-mini models.  
Look for 🛠 to run existing notebooks with *new dependency versions and platform API constraints and tweaks.*

## [October 30, 2024]

### Added
`Chapter06/KantaiBERT.ipynb` and `Chapter06/Customer_Support_for_X.ipynb` enhancement:    
**wandb.ai training metrics** added while training. 
You can now view your model's metrics on **Hugging Face**.

### Upgraded      

#### Upgrade #1 Vertex AI
`Chapter14/Google_Vertex_AI.ipynb` has now been upgraded to `Chapter14/Google_Vertex_AI_Gemini.ipynb` with the `gemini-1.5-flash-001` model. 
A timer has been added to adapt to the API call rates.
It is recommended to read `Google_Vertex_AI.ipynb` with the chapter in the book to understand the process but then to run `Google_Vertex_AI_Gemini.ipynb` which now calls 20 LLM tasks and a computer vision task.

#### Upgrade #2 Stable Diffusion

Open and Read `Chapter17/Stable_Diffusion_Keras.ipynb` with the book to understand the process. However, this notebook has been replaced by 
`Chapter17/Stable_Diffusion_Hugging_Face.ipynb`.

**Reason for Change**: The initial implementation using `keras_cv` for Stable Diffusion was unstable due to compatibility issues between **Keras** and **TensorFlow**. Specifically, there were multiple shape mismatch errors, difficulties in managing precision (mixed vs float32), and challenges in manually encoding prompts due to limitations in `keras_cv`'s API. These issues led to unreliable behavior and a frustrating development experience in Google Colab.

**New Approach**: We transitioned to using **Hugging Face's Diffusers library** for Stable Diffusion because it provides a more stable and intuitive workflow for generating images from text prompts. The `diffusers` library integrates well with **PyTorch** and has comprehensive support for text-to-image generation. It allowed us to seamlessly encode prompts and use GPU acceleration without running into the issues present in the Keras implementation.

**Benefits**:
- Improved compatibility and stability.
- Easier to manage the text encoding and image generation workflow.
- Robust GPU utilization through PyTorch, leading to faster and more reliable results.
- Clearer API with better community support for addressing issues.

This change ensures a smoother experience when working with Stable Diffusion in Google Colab, resulting in faster image generation and more predictable outputs.

#### Upgrade #3 Diffusion videos

Diffusion models have evolved tremendously in a very short time, from the ability to create animations to generating videos and more. The code in this `Chapter17/Stable__Vision_Stability_AI_Animation.ipynb` notebook contains a Stability SDK, which is interesting to read along with the book. 

Then, you can access (open source and free, of course!) the recent developments of text-to-video technology in the RAG-Driven Generative AI repo starting with the first notebook of [`Chapter 10, RAG for Video Stock Production with Pinecone and OpenAI`](https://colab.research.google.com/github/Denis2054/RAG-Driven-Generative-AI/blob/main/Chapter10/Video_dataset_visualization.ipynb)



### Fixed 
Fixed typo in `Chapter04/WMT_translations.ipynb`:   
Now, "smoothing" is correctly written in one of the print instructions.

### Performance
`Chapter 16/ViT_CLIP.ipynb`:  
The `Feature extractor simulator` section automatically displays all the patches to give a full view of feature extraction. 


