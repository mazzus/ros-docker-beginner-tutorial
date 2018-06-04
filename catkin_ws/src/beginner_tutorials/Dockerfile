# Use the ros-kinetic-base image as a base image. This image already contains all nessecary dependencies for running ros
FROM ros:kinetic-ros-core

# The default shell is sh, switching to bash makes it easier to work with ros
SHELL ["/bin/bash", "-c"]

# Create a working directory for the catkin workspace
WORKDIR /catkin_ws

# Copy the cide of the beginner tutorials folder into the catkin workspace
# COPY has the syntax COPY path/on/host/machine /path/inside/docker/image
COPY . src/beginner_tutorials

# Build our package using catkin_make
RUN source /opt/ros/kinetic/setup.bash && catkin_make

# Move the entry script to root
RUN mv src/beginner_tutorials/docker_entry_script.sh /
# Make the entry script executable
RUN chmod +x /docker_entry_script.sh

# Create an entrypoint, the entryscript will source all neded setup files for ros to work properly.
ENTRYPOINT [ "/docker_entry_script.sh" ]