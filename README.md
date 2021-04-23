# Exploring Super-Convergence in Analog Hardware Acceleration Kit for In-memory Computing Design

Abstract: Deep neural networks, a popular AI/ML algorithm, have achieved promising results in recent years in many complex tasks such as image/speech recognition and adaptive AI responses in game engines. However, training large DNN is considered a computationally intensive task that demands extensive use of computational resources for days at a time. One reason being is that the computation and memory endpoints are in different locations on a chip, and data is transferred back and forth between storage and computation units frequently. This phenomenon is known as the so-called Von Neumann's bottleneck which prevents a system from achieving real-time and energy-efficient computations. Thus, to mitigate this bottleneck and accelerate the training time, we propose to implement a hardware-software co-optimization approach with in-memory computing architectures and the super-convergence algorithm.


# Data usage

If you guys have any questions regarding the different colabs used please refer to the points below:

- ECSE552_Project colab - contains our NN training with Analog Hardware Acceleration Kit for super convergence and normal training

- super_convergence colab - contains our super convergence NN training using only Pytorch framework also contains super convergence algorithm vs normal training

- aihwkit_installation colab - Run this colab if you guys want to build the Analog Hardware Acceleration Framework (IBM) from source and the binary would be built with CUDA support to enable GPU training. https://aihwkit.readthedocs.io/en/latest/ advanced_install.html for more information.
