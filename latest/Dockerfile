## -*- docker-image-name: "trileg/docker-webtex" -*-
FROM trileg/arch-base:latest
MAINTAINER Kensuke Kosaka <kosaka@trileg.net>

RUN pacman -Syu --noconfirm fakeroot python texlive-langcjk poppler git &> /dev/null
USER user
RUN yaourt -Syua --noconfirm jdk &> /dev/null

WORKDIR /home/user/
RUN curl -L -O --silent https://bootstrap.pypa.io/get-pip.py && \
  python get-pip.py --user > /dev/null && \
  rm -f get-pip.py
ENV PATH $PATH:/home/user/.local/bin
RUN git clone https://github.com/trileg/WebTeX.git &> /dev/null
WORKDIR /home/user/WebTeX/
RUN pip install --user -r pip-requirements.txt > /dev/null

RUN curl --silent -L -o /tmp/ace.tar.gz https://github.com/ajaxorg/ace-builds/archive/v1.2.3.tar.gz && \
  mkdir /tmp/ace-builds && \
  tar -xvf /tmp/ace.tar.gz -C /tmp/ace-builds --strip-components 1 > /dev/null && \
  rm -f /tmp/ace.tar.gz && \
  mkdir /home/user/WebTeX/WebTeX/static/ace-builds && \
  mv /tmp/ace-builds/src-noconflict /home/user/WebTeX/WebTeX/static/ace-builds/ && \
  rm -rf /tmp/ace-builds

RUN curl --silent -L -o /tmp/redpen.tar.gz https://github.com/redpen-cc/redpen/releases/download/redpen-1.6.0/redpen-1.6.0.tar.gz && \
  mkdir /home/user/redpen && \
  tar -xvf /tmp/redpen.tar.gz -C /home/user/redpen --strip-components 1 > /dev/null && \
  rm -f /tmp/redpen.tar.gz
ENV PATH $PATH:/home/user/redpen/bin
