# Edge AI Deployment Research

An exploratory project covering YOLOv8n-based chicken detection and model conversion with ST Edge AI for the STM32N6570-DK.


## Background

After building several computer-based AI vision projects (like the Virtual Violin in my other repositories), I realized a major limitation: they all relied on my computer’s CPU. For real-world interactions and applications, I definitely needed dedicated hardware. Coincidentally, I had the opportunity to connect with a brilliant professor who is specialized in the embedded systems field. 

To convince him that I was capable of handling professional-level projects, I spent a lot of time studying neural network fundamentals and the hardware features of the STM32N657. He then provided me with a guideline on how to deploy models to the STM32N6570-DK, along with a labeled dataset of 7,600+ images to train a custom computer vision model using YOLO. 

The process was incredibly challenging. I struggled quite a bit because the official guidelines were not fully adapted to my computer's specific environment, leading to a huge number of configuration errors and dependency conflicts. For instance, I had to debug frustrating path mismatches in the configuration files that constantly crashed the pipeline. However, through days of hard work, researching documentation, and trial-and-error, I managed to resolve the environment issues.

I trained a YOLOv8n (Nano) model on the chicken dataset in a CPU-only environment, achieving an mAP@50 of 81.9%. I also worked with the ST Edge AI toolchain to generate C-language network files from an ONNX model. The archived ONNX and C files describe a two-class image classifier, while the sample images document the YOLOv8n chicken-detection experiment.

Without access to a physical STM32N6 board, I did not carry out on-board testing. These training and model-conversion exercises gave me practical experience with edge AI development and later inspired me to build a MaixCAM-based hardware prototype.

## What's in this Repository?

Instead of uploading gigabytes of training datasets, this repository serves as a Research Archive containing the ultimate "proof of work" files:

* Research Report_ YOLO-based Vi...: My full bilingual (English & Chinese) research report detailing the methodology, hardware architecture analysis, and debugging process.
* **sample_picture1.jpg & sample_picture2.jpg:** Example detection outputs from the YOLOv8n chicken-detection experiment.
* **my_model_OE_3_3_1.onnx:** An archived two-class image-classification model used in the ST Edge AI conversion exercise, with a 96×96 image input.
* **stai_network.c & stai_network.h:** ST-generated interface code and tensor metadata corresponding to the archived two-class ONNX model.
* network_atonbuf.xSPI2.raw: The final binary memory file ready to be flashed into the external XSPI Flash of the STM32N6.

---

> ### Author's Declaration
> The conceptual framework and dataset were provided by the supervising professor. The software engineering, model training, debugging, and ONNX conversion were carried out by the author and owner of this GitHub repository, with reference to relevant technical documentation and development resources.
