<p align="center">
  <a href="https://summerofcode.withgoogle.com">
    <img src="https://summerofcode.withgoogle.com/assets/media/logo.svg" alt="GSoC Logo" height="75">
  </a>
  <a href="https://dora-rs.ai">
    <img src="https://raw.githubusercontent.com/dora-rs/dora/main/docs/src/logo.svg" alt="dora-rs Logo" height="75">
  </a>
</p>

# Google Summer of Code 2025 – Final Work Submission

## Table of Contents
- [Google Summer of Code 2025 – Final Work Submission](#google-summer-of-code-2025--final-work-submission)
  - [Table of Contents](#table-of-contents)
  - [Project Overview](#project-overview)
  - [Project Abstract](#project-abstract)
  - [Project Goals](#project-goals)
  - [Work Done](#work-done)
  - [Current State](#current-state)
  - [Future Work](#future-work)
  - [Links and Resources](#links-and-resources)
  - [Datasets and Models](#datasets-and-models)
  - [Acknowledgements](#acknowledgements)

## Project Overview
**Project:** Robot Data Collection Improvement  
**Contributor:** Shashwat Patil  
**Organization:** Dora-rs  
**Mentors:** Haixuan Xavier Tao  

## Project Abstract

This project focuses on improving robot data collection by developing an easy-to-use, end-to-end system centered around the **Dora platform**. The system leverages the **SO-101 follower-leader robotic arm pair**, an affordable and accessible hardware setup.

Data collection nodes were implemented in Dora using the widely adopted **LeRobot dataset format**, ensuring compatibility with modern robotics pipelines. Comprehensive tutorials and documentation were created to help the community replicate the setup and contribute datasets. The collected dataset has been made publicly available to foster **open-source collaboration** and advance reproducibility in robotics research.

## Project Goals

- **Data Collection System**: Build an end-to-end, low-cost setup for robot data collection centered around the **Dora platform**.

- **Simulation & Real-world Integration**: Develop a **MuJoCo simulation environment** alongside real hardware to enable both simulated and physical data collection.

- **Standardized Data Format**: Implement data collection nodes in Dora following the widely used **LeRobot dataset format**, ensuring compatibility with modern ML and robotics pipelines.

- **Open-source Dataset Creation**: Generate and share a diverse dataset of manipulation tasks, covering both teleoperated and autonomous modes, to support research and model training.

- **Community Resources**: Provide comprehensive tutorials, documentation, and walkthroughs to help the community replicate the system, customize it, and contribute their own datasets.

- **Benchmarking with VLA Models (Extended Goal)**: As an extension beyond the original plan, datasets were evaluated using **vision-language-action models** such as **NVIDIA Groot** and **OpenPi Pi0**, demonstrating their applicability in real manipulation tasks.

## Work Done

- **MuJoCo Simulation Node for Robotic Control**
  - Developed a `dora-mujoco` node enabling control of various robot arms (e.g., Franka Emika Panda, UR5e, SO-101) using configuration-driven YAML nodes and `robot-descriptions` for URDF loading without manual asset management.
  - Created examples demonstrating how to build an IK chain with **dora-pytorch-kinematics**, compute **Forward/Inverse Kinematics**, and perform simple path planning on robotic arms.

- **Dataset Collection Node**
  - Implemented a data collection node in Dora that records joint states and multi-camera video streams, packaged in the widely used **LeRobot dataset format** for compatibility with ML pipelines (e.g., PyTorch, Hugging Face).
  - Integrated live keyboard controls to manage recording sessions (`n` for next episode, `r` to re-record, `q` to quit).
  - Produced a complete YouTube tutorial featuring the **SO-101 follower-leader arm**, covering dataset recording, training an ACT policy with LeRobot, and running inference via the `dora-policy-inference` node.

- **Inference Node and Model Integration**
  - Developed the `dora-policy-inference` node to run trained policies directly within Dora pipelines.
  - Evaluated dataset performance by training and fine-tuning **VLA models (NVIDIA Groot, OpenAI Pi0)** and deploying them on the **SO-101 arm** for table-cleaning tasks.
  - Enhanced inference logic to synchronize multi-camera streams before execution, ensuring stable and reliable policy runs.

Additionally, I collected data using the **SO-101 robot**, building a comprehensive dataset of **table-cleaning tasks** with miscellaneous objects. This dataset was subsequently used to train and fine-tune **ACT Policy**, **NVIDIA Groot**, and **OpenAI Pi0** models. All trained models have been uploaded for community use on Hugging-Face.

## Current State

The project has been successfully completed with all core goals achieved:

- **Simulation**: A MuJoCo-based simulation environment is working, with examples for generic arms (Franka, UR5e, SO-101). FK/IK and path planning examples using `dora-pytorch-kinematics` are implemented and tested.  
- **Dataset Collection**: The Dora dataset node records joint states and multi-camera streams in the **LeRobot format**. Interactive keyboard commands are integrated, and a full tutorial with the SO-101 arm (recording, training ACT, running inference) is complete.
- **Inference**: The `dora-policy-inference` node can run ACT policies trained on the collected dataset. Groot and Pi0 VLA models have been successfully trained/finetuned on SO-101 table-cleaning tasks and evaluated.  
- **Open Source Contributions**: Tutorials, documentation, dataset, and trained models are publicly available.

## Future Work

- **Dataset Expansion**: Collect larger, more diverse datasets across different tasks and robotic arms, and extend onto different robotic platforms.
- **Extended Benchmarking**: Evaluate additional VLA and policy learning models beyond ACT, Groot, and Pi0.

Feel free to fork the repository and submit pull requests. For major changes, please open an issue to discuss your ideas first. Contributions are always welcomed!

## Links and Resources

- [GSoC Project Page](https://summerofcode.withgoogle.com/programs/2025/projects/JzWj3E87)
- [Dora-rs Repository](https://github.com/dora-rs/dora)
- [My Merged Pull Requests](https://github.com/dora-rs/dora/pulls?q=is%3Amerged+is%3Apr+author%3AShashwatPatil+)
- [YouTube Tutorial – Dataset Collection & Inference Demo](https://www.youtube.com/watch?v=jFP8UAtz4sg)
- [GR00T and Openpi Pi0 Comparison](https://github.com/ShashwatPatil/VLA_model_comparision/blob/master/vla_model_comparison.md)

## Datasets and Models

**Training Dataset:** https://huggingface.co/datasets/SGPatil/so101_table_cleanup  
**Test Dataset:** https://huggingface.co/datasets/SGPatil/so101_table_cleanup_2  

**Pi0 LoRA Fine-tuned Model:** https://huggingface.co/SGPatil/pi0_so101_table_cleanup_checkpoints  
**Gr00t Fine-tuned Model:** https://huggingface.co/SGPatil/GR00T-N1.5-SO101-finetune-table-cleanup  

**Evaluation Results for Pi0:** https://huggingface.co/SGPatil/eval_pi0_so101  
**Evaluation Results for Gr00t:** https://huggingface.co/SGPatil/eval_groot_n1.5_so101

## Acknowledgements

I would like to express my heartfelt gratitude to my mentor **Haixuan Xavier Tao** for his invaluable guidance, continuous support, and insightful feedback throughout this GSoC journey. His expertise and encouragement were instrumental in making this project a success.

Special thanks to the **Dora-rs community** and **Google Summer of Code** for making this work possible.

I’m grateful to the open-source community for their contributions and feedback throughout this project, and I hope the outcomes will serve as a foundation that others can build on to advance accessible robotics research.