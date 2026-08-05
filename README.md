# Edge AI Deployment Research

A research project focused on training a lightweight computer vision model and executing the complete preliminary preparation for deployment on the STM32N6570-DK embedded NPU.

## Background

After building several computer-based AI vision projects (like the Virtual Violin in my other repositories), I realized a major limitation: they all relied on my computer’s CPU. For real-world interactions and applications, I definitely needed dedicated hardware. Coincidentally, I had the opportunity to connect with a brilliant professor who is specialized in the embedded systems field. 

To convince him that I was capable of handling professional-level projects, I spent a lot of time studying neural network fundamentals and the hardware features of the STM32N657. He then provided me with a guideline on how to deploy models to the STM32N6570-DK, along with a labeled dataset of 7,600+ images to train a custom computer vision model using YOLO. 

The process was incredibly challenging. I struggled quite a bit because the official guidelines were not fully adapted to my computer's specific environment, leading to a huge number of configuration errors and dependency conflicts. For instance, I had to debug frustrating path mismatches in the configuration files that constantly crashed the pipeline. However, through days of hard work, researching documentation, and trial-and-error, I managed to resolve the environment issues.

I successfully trained a YOLOv8n (Nano) model in a pure CPU environment, achieving an mAP@50 of 81.9%. Then, I bridged the gap between Python (PyTorch) and C (STM32CubeIDE) using ONNX and ST Edge AI, successfully generating the C-language neural network code without errors.

Although I didn't have the physical STM32N6 board on hand to flash the final binary, completing this entire software and firmware integration pipeline was a huge theoretical breakthrough for me. It eventually inspired me to buy a MaixCAM board and build a physical hardware prototype (a super cool AI spectacle).

## What's in this Repository?

Instead of uploading gigabytes of training datasets, this repository serves as a Research Archive containing the ultimate "proof of work" files:

* Research Report_ YOLO-based Vi...: My full bilingual (English & Chinese) research report detailing the methodology, hardware architecture analysis, and debugging process.
* sample_picture1.jpg & sample_picture2.jpg: Visual proof of the YOLOv8n model successfully identifying "healthy" and "unhealthy" chickens.
* my_model_OE_3_3_1.onnx: The PyTorch model successfully exported to the ONNX intermediate format.
* stai_network.c & stai_network.h: The absolute core of this project. This is the neural network mathematically translated into C-language arrays and pointers by the ST Edge AI Core toolchain.
* network_atonbuf.xSPI2.raw: The final binary memory file ready to be flashed into the external XSPI Flash of the STM32N6.

---

> ### Author's Declaration
> The conceptual framework and dataset were provided by the supervising professor. The software engineering, model training, debugging, and ONNX conversion were carried out by the author and owner of this GitHub repository, with reference to relevant technical documentation and development resources.
