<p align="center">
  <a href="https://summerofcode.withgoogle.com">
    <img src="https://summerofcode.withgoogle.com/assets/media/logo.svg" alt="GSoC Logo" height="75">
  </a>
  &nbsp;&nbsp;
  <a href="https://dora-rs.ai">
    <img src="https://raw.githubusercontent.com/dora-rs/dora/main/docs/src/logo.svg" alt="dora-rs Logo" height="75">
  </a>
</p>



# Google Summer of Code 2025 – Final Work Submission


## Project: Robot Data Collection Improvement 
**Contributor:** Shashwat Patil
**Organization:** Dora-rs
**Mentors:** Haixuan Xavier Tao

## Project Abstract

This project focuses on improving robot data collection by developing an easy-to-use, end-to-end system centered around the **Dora platform**. The system leverages the **SO-101 follower-leader robotic arm pair**, an affordable and accessible hardware setup.  

Data collection nodes were implemented in Dora using the widely adopted **LeRobot dataset format**, ensuring compatibility with modern robotics pipelines. Comprehensive tutorials and documentation were created to help the community replicate the setup and contribute datasets. The collected dataset has been made publicly available to foster **open-source collaboration** and advance reproducibility.  

## Project Goals

- **Data Collection System**: Build an end-to-end, low-cost setup for robot data collection centered around the **Dora platform**.

- **Simulation & Real-world Integration**: Develop a **MuJoCo simulation environment** alongside real hardware to enable both simulated and physical data collection.  

- **Standardized Data Format**: Implement data collection nodes in Dora following the widely used **LeRobot dataset format**, ensuring compatibility with modern ML and robotics pipelines.

- **Open-source Dataset Creation**: Generate and share a diverse dataset of manipulation tasks, covering both teleoperated and autonomous modes, to support research and model training.

- **Community Resources**: Provide comprehensive tutorials, documentation, and walkthroughs to help the community replicate the system, customize it, and contribute their own datasets.  

- **Benchmarking with VLA Models (Extended Goal)**: As an extension beyond the original plan, datasets were evaluated using **vision-language-action models** such as **NVIDIA Groot** and **OpenPi Pi0**, showcasing their applicability in real manipulation tasks.

## Work Done

### Key Features Implemented

- **MuJoCo Simulation Node for Robotic Control**  
  - Added a `dora-mujoco` node enabling control of robot arms (e.g., Franka Emika Panda, UR5e, SO-101 etc.) using configuration-driven YAML nodes and `robot-descriptions` for URDF loading without manual asset management.  
  - Added examples showing how to build an IK chain with **dora-pytorch-kinematics**, compute **FK/IK**, and perform simple path planning on an arm.

- **Dataset Collection Node**  
  - Implemented a data collection node in Dora that records joint states and multi-camera video streams, packaged in the widely used **LeRobot dataset format** for compatibility with ML pipelines (e.g., PyTorch, Hugging Face).  
  - Added live keyboard controls to manage recording sessions (`n` for next episode, `r` to re-record, `q` to quit).  
  - Created a full YouTube tutorial with the **SO-101 follower-leader arm**, covering dataset recording, training an ACT policy with LeRobot, and running inference via the `dora-policy-inference` node.

- **Inference Node and Model Integration**  
  - Implemented the `dora-policy-inference` node to run trained policies directly on Dora pipelines.  
  - Evaluated dataset performance by training/finetuning **VLA models (NVIDIA Groot, OpenPi Pi0)** and deploying them on the **SO-101 arm** for table-cleaning tasks.  
  - Improved inference logic to synchronize multi-camera streams before execution, ensuring stable and reliable policy runs.

I also collected data on the **SO-101 robot**, building a simple dataset of **table-cleaning tasks** with miscellaneous objects. The dataset was later used to train and finetune **ACT Policy**, **NVIDIA Groot** and **OpenPi Pi0**, and the trained models have been uploaded for community use.


## Current State

The project is complete and fully functional with all core goals achieved

- **Simulation**: A MuJoCo-based simulation environment is working, with examples for generic arms (Franka, UR5e, SO-101). FK/IK and path planning examples using `dora-pytorch-kinematics` are implemented and tested.  
- **Dataset Collection**: The Dora dataset node records joint states and multi-camera streams in the **LeRobot format**. Interactive keyboard commands are integrated, and a full tutorial with the SO-101 arm (recording, training ACT, running inference) is complete.
- **Inference**: The `dora-policy-inference` node can run ACT policies trained on the collected dataset. Groot and Pi0 VLA models have been trained/finetuned on SO-101 table-cleaning tasks and evaluated successfully.  
- **Open Source Contributions**: Tutorials, documentation, dataset, and trained models are published on huggingface.

## What’s Left To Do

- **Dataset Expansion**: Collect larger, more diverse datasets across different tasks and robotic arms.
- **Extended Benchmarking**: Evaluate additional VLA and policy learning models beyond ACT, Groot, and Pi0.

## Links

[GSoC Project Page](https://summerofcode.withgoogle.com/programs/2025/projects/JzWj3E87)
[Dora-rs](https://github.com/dora-rs/dora)
[My Merged PRs](https://github.com/dora-rs/dora/pulls?q=is%3Amerged+is%3Apr+author%3AShashwatPatil+)
[YouTube Tutorial – Dataset Collection & Inference Demo](https://www.youtube.com/watch?v=jFP8UAtz4sg)



## Resources

Train Dataset: https://huggingface.co/datasets/SGPatil/so101_table_cleanup     
Test Dataset: https://huggingface.co/datasets/SGPatil/so101_table_cleanup_2    

Pi0 lora fine-tuned model: https://huggingface.co/SGPatil/pi0_so101_table_cleanup_checkpoints   
Gr00t fine-tuned model: https://huggingface.co/SGPatil/GR00T-N1.5-SO101-finetune-table-cleanup

evaluation results for pi0: https://huggingface.co/SGPatil/eval_pi0_so101   
evaluation results for gr00t: https://huggingface.co/SGPatil/eval_groot_n1.5_so101
