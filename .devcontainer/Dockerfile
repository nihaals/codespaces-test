FROM orangutan/playground:ubuntu-20.04

ARG USERNAME=user
ARG USER_UID=1000
ARG USER_GID=$USER_UID

ENV SHELL /bin/bash

RUN export DEBIAN_FRONTEND=noninteractive \
&& apt-get update \
&& apt-get install -y \
    python3 \
    python3-pip \
    python3-venv \
&& pip3 install -U pip \
&& pip3 install -U poetry \
&& groupadd --gid $USER_GID $USERNAME \
&& useradd -mrs /bin/bash --uid $USER_UID --gid $USER_GID $USERNAME \
&& echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
&& chmod 0440 /etc/sudoers.d/$USERNAME
USER $USERNAME
CMD ["/bin/bash"]
