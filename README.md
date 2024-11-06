# Cloud Infrastructure & Architecture Lab Exercises

This repository contains exercises from the **Cloud Infrastructure & Architecture Lab** course. Each exercise focuses on a different aspect of cloud infrastructure management using OpenStack, from setting up nodes to configuring storage and managing environments for multiple users.

## Table of Contents

1. [Exercise 1: Configure NOVA Compute Node](ex1-Configure_NOVA_compute_Node.md)
2. [Exercise 2: Configure Swift Object Storage](ex2-Configure_Swift_object_storage.md)
3. [Exercise 3: Construct a Cinder Block Node](ex3-Construct_a_cinder_block_node.md)
4. [Exercise 4: Build a Horizon Node](ex4-Build_a_horizon_node.md)
5. [Exercise 5: Launching an Instance](ex5-Launching_an_instance.md)
6. [Exercise 6: Sharing Project Environment](ex6-Sharing_project_environment.md)

## Overview

This lab manual provides step-by-step instructions for configuring various components within a cloud infrastructure environment using OpenStack. Each exercise file is structured as follows:

- **Aim**: Objective of the exercise.
- **Procedure**: Detailed steps and commands to achieve the setup.

## Getting Started

To use these exercises:

1. Clone this repository to your local machine:
    ```bash
    git clone https://github.com/raguladhithyam/Cloud-Infrastructure-and-Architecture.git
    ```
2. Open the `.md` file corresponding to the exercise you want to perform and follow the instructions.

## Exercises

### Exercise 1: Configure NOVA Compute Node
Set up the NOVA compute node on OpenStack to manage virtual machine instances. Detailed setup steps and prerequisites are included.

### Exercise 2: Configure Swift Object Storage
Configure Swift, OpenStack’s object storage service, which enables scalable and redundant storage of data across clusters.

### Exercise 3: Construct a Cinder Block Node
Build a Cinder Block Storage Node for OpenStack to provide block storage for virtual instances. This involves database configuration, service credential setup, and endpoint creation.

### Exercise 4: Build a Horizon Node
Install and configure the OpenStack dashboard, known as Horizon, to monitor and manage cloud resources.

### Exercise 5: Launching an Instance
Instructions for launching a virtual machine instance in OpenStack, including key pair setup, security groups, and instance configuration.

### Exercise 6: Sharing Project Environment
Share project resources and environments with multiple users. This exercise covers user management, role assignment, and project configurations in OpenStack.

## Prerequisites

Each exercise requires:
- Ubuntu 22.04 LTS as the operating system.
- An OpenStack environment set up with necessary modules.
- Access to OpenStack CLI for administrative tasks.

## Note
For additional details, refer to the [Word Document](https://docs.google.com/document/d/1I30pxRXYx3BRxkGLBs9729-d6cC3LMxm/edit?usp=sharing&ouid=106960513552409389091&rtpof=true&sd=true).

## Contributing

Feel free to contribute to this repository by adding improvements or suggestions. Please create a pull request with detailed information on your changes.
