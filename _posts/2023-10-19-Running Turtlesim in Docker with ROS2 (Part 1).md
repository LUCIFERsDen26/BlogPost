# Running Turtlesim in Docker with ROS2 (Part 1)

Let's dive into running Turtlesim using ROS2 within a Docker container. We'll assume that you already have Docker installed and have successfully run a "Hello, World!" container. If you haven't, go ahead and give it a try - nothing's holding you back!

By following this guide, you'll pull a ROS2 Docker image from the Docker Hub, create a container, and access it through multiple terminal windows, making your ROS2 development a breeze.

For this guide, we'll be using Linux Ubuntu 22.04, as it's known for its ease of use in the world of containerization and also as host.

## Getting Started

Open your terminal on your Ubuntu host and run the following commands:

```bash
export DISPLAY=:1.0
xhost +local:docker
```

If you plan to do this frequently, it's a good idea to add these commands to your `~/.bashrc` file to have them readily available every time you open a new terminal session.

## Pulling the Docker Image

Now, let's pull the ROS2 Docker image from Docker Hub. Run the following command in your Linux terminal:

```bash
sudo docker pull osrf/ros:humble-desktop
```

This command fetches the "humble-desktop" distribution of ROS2 for your use.

## Creating the Docker Container

To create a Docker container, use the following command:

```bash
sudo docker run -it --name ros2 --net=host --device /dev/dri/ -e DISPLAY=$DISPLAY -v $HOME/.Xauthority:/root/.Xauthority:ro osrf/ros:humble-desktop
```

Let's break down this command:

- `sudo docker run`: This command starts a Docker container from an image.
- `-it`: These options enable an interactive terminal session, allowing you to interact with the container.
- `--name ros2`: Assigns the name "ros2" to your Docker container for easy reference.
- `--net=host`: Shares the host's network stack with the container, facilitating network communication.
- `--device /dev/dri/`: Grants access to Direct Rendering Infrastructure (DRI) devices, essential for graphics rendering.
- `-e DISPLAY=$DISPLAY`: Sets the `DISPLAY` environment variable to enable GUI applications to connect to your host's display.
- `-v $HOME/.Xauthority:/root/.Xauthority:ro`: Mounts the X server authentication file for Xhost authentication in read-only mode.
- `osrf/ros:humble-desktop`: Specifies the Docker image containing the ROS2 environment for "humble-desktop."

With this command, you create a container named "ros2" and enter its Bash shell. To exit the shell, press `Ctrl + D`.

## Restarting the Container

If you need to restart your "ros2" container after rebooting your PC, first check if it's still there by running:

```bash
sudo docker ps
```

To see all containers, including those that are not running:

```bash
sudo docker ps -a
```

If you find the "ros2" container, start it using:

```bash
sudo docker start ros2
```

## Accessing the Bash Shell

To open a new Bash shell within the "ros2" container in multiple windows, use:

```bash
sudo docker exec -it ros2 bash
```

This command allows you to interact with the running Docker container in an interactive shell. It's particularly useful for debugging, maintenance, and executing specific tasks within the container.

## Using ROS2

To use ROS2 in the terminal, run:

```bash
source /opt/ros/humble/setup.bash
```

By sourcing this script, you make ROS2 tools and libraries for the "humble" distribution available in your current shell session. Now you can work with ROS packages, launch ROS nodes, and use ROS-specific tools related to the "humble" distribution.


**References:**
- [Official ROS Documentation](https://docs.ros.org/en/humble/How-To-Guides/Run-2-nodes-in-single-or-separate-docker-containers.html)
- [Medium Guide](https://robofoundry.medium.com/trying-out-ros2-humble-hawksbill-using-docker-4490bc88c926)
- [Docker Commands](https://www.knowledgehut.com/blog/devops/basic-docker-commands)
- [Top Essential Docker Commands](https://www.mygreatlearning.com/blog/top-essential-docker-commands/)
