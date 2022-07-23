# TensorFlow + GPU support

Base container for TensorFlow with GPU support and jupyter-server installed

This image includes OpenCV for image manipulations

## Usage:

Start the docker container:

```docker run --rm -it --runtime=nvidia <image_name>[:tag]```

To create a non-volatile contaier use:

```docker run -d -it --runtime=nvidia --name=<contaainer_name> <image_name>[:tag]```

If you need a jupyter-lab instances to work with, within the container use:

```$ jupyter-lab --ip=0.0.0.0```

This command creates a jupyter-lab session with a unique token. In order to navigate to the webpage docker port mapping is required. You need to add ```-p 8888:8888``` to you docker run command. The full command is the following:

```docker run -d -it -p 8888:8888 --runtime=nvidia --name=<contaainer_name> <image_name>[:tag]```

Is then often useful to mount a local share on docker: use ```-v <path_to_local_share>:<path_to_mnt_directory>``` on docker run command