FROM python:3.11.3-bullseye

RUN groupadd --gid 1000 devops \
    && useradd --uid 1000 --gid 1000 -m -s /bin/bash devops \
    && apt-get update \
    && apt-get install -y sudo iputils-ping vim \
    && echo devops ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/devops \
    && chmod 0440 /etc/sudoers.d/devops 

USER devops
WORKDIR /home/devops/
ENV VIRTUALENV=/home/devops/venv
RUN python3 -m venv $VIRTUALENV
ENV PATH="$VIRTUALENV/bin:$PATH"
RUN python -m pip install --upgrade pip && python -m pip install black flake8 mypy pytest isort bandit pylint autopep8 yapf

