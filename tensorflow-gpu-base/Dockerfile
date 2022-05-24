from tensorflow/tensorflow:latest-gpu

COPY packages packages
COPY python_packages python_packages

# Install additional packages
RUN apt-get update -q -y \
    && apt-get install -y $(cat packages)

# Create user
ARG CONTAINER_USER="docker_user"
ARG CONTAINER_USER_WD="/home/${CONTAINER_USER}"

RUN useradd -ms /bin/bash ${CONTAINER_USER}

# Set user
USER ${CONTAINER_USER}
WORKDIR ${CONTAINER_USER_WD}

# Upgrade pip
RUN /usr/bin/python3 -m pip install --upgrade pip

# Install jupyterlab
RUN pip install jupyterlab

ENV PATH="${CONTAINER_USER_WD}/.local/bin:${PATH}"

# Install additional python packages
RUN pip install -r /python_packages

CMD ["/bin/bash"]