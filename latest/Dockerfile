## -*- docker-image-name: "trileg/docker-webtex" -*-
FROM trileg/arch-base:latest
MAINTAINER Kensuke Kosaka <k@trileg.net>

RUN pacman -Syu --noconfirm jre8-openjdk-headless python texlive-langcjk poppler &> /dev/null

USER user
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

ADD scripts/run.sh /home/user/WebTeX/
RUN sudo chmod +x /home/user/WebTeX/run.sh
CMD /home/user/WebTeX/run.sh &> /dev/null
RUN rm -f /home/user/WebTeX/run.sh
