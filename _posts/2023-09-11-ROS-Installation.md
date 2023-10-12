---
layout: post
title:  "Installing ROS2 in Docker GUI using Xhost"
author: Bhushan
categories: [ ROS, tutorial, Installation ]
image: "https://i0.wp.com/roboticseabass.com/wp-content/uploads/2023/07/docker_ros2_banner.png?fit=1122%2C519&ssl=1&auto=format&fit=crop&w=750&q=80"
featured: true
hidden: false
---

Hello, guys! Let's say you want to learn ROS. You start by searching online and come to the conclusion that you need a dual boot PC or laptop with Ubuntu installed to run ROS1 or ROS2. But, there's always that "but". Anyway! I have some ways that you can install ROS in less than 20-30 minutes (depending on your internet connection).

So, here's the big question: how?

## Docker Installation on Ubuntu

Let's dive in. Let's say you already have Linux installed. Now all you need is Docker. If you want to learn more, click [here](https://cloudcone.com/docs/article/how-to-install-docker-on-ubuntu-22-04-20-04/). This is the official website for installing Docker on Ubuntu, and you are good to go!

## Installing ROS Docker Image

After installing Docker, you need an image of ROS to run a container. I know exactly where to find the steps to do that. They are right [here](http://wiki.ros.org/docker/Tutorials/Docker). The installation link is for ROS Neotic; for ROS 2, change "neotic" to "humble".

## Docker Setup on Windows

But for Windows users... Oh, come on, guys! Initially, you search for the best operating system to run ROS and come to the conclusion yourself (obviously joking).

At first, you have to install WSL (Windows Subsystem for Linux) on your machine. How, you ask? [Like this](https://www.how2shout.com/how-to/how-to-install-ubuntu-22-04-on-windows-11-or-10-wsl.html). You also need to install the graphics driver on WSL, so use this [link](https://www.linuxcapable.com/install-nvidia-drivers-on-ubuntu-linux/#Section-3-Install-NVIDIA-Drivers-with-Ubuntu-Repository-using-CLI). Note: only do autoinstall and reboot, no need for a specific version. It will install the latest version. After that, head on to the official website and download the official Docker desktop. It could run on the first try, but (this "but"!) you may get some errors like hypervisor not enabled or something. Search it on YouTube and follow the steps.

## Working with ROS Docker Container

Let's assume you've downloaded the ROS image, and now you want to create a container of that image. In simple, very simple words, an Xhost-enabled container can render the GUI on the host machine using the NVIDIA graphics card. Check out [xhost](https://robofoundry.medium.com/trying-out-ros2-humble-hawksbill-using-docker-4490bc88c926) for more details.
