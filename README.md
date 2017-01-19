# docker-webtex
[![Build Status](https://travis-ci.org/trileg/docker-webtex.svg?branch=master)](https://travis-ci.org/trileg/docker-webtex)
[![](https://images.microbadger.com/badges/image/trileg/docker-webtex.svg)](http://microbadger.com/images/trileg/docker-webtex "Get your own image badge on microbadger.com")
[![](https://images.microbadger.com/badges/version/trileg/docker-webtex.svg)](http://microbadger.com/images/trileg/docker-webtex "Get your own version badge on microbadger.com")
[![AMA](https://img.shields.io/badge/ask%20me-anything-0e7fc0.svg)](https://github.com/trileg/ama)

Web-based LaTeX editor and compiler in an Arch Linux docker container.

WebTeX build status: [![Build Status](https://travis-ci.org/trileg/WebTeX.svg?branch=master)](https://travis-ci.org/trileg/WebTeX)

## How to use this?
#### Pull docker image from Docker Hub
```
$ docker pull trileg/docker-webtex:latest
```

#### Run container from this pulled image
```
$ docker run -itd -p 8080:8080 trileg/docker-webtex:latest /bin/bash -c "python /home/user/WebTeX/WebTeX/app.py"
```

#### Access WebTeX by your preferred browser
```
http://localhost:8080/
```

#### Sign in to WebTeX by using default user name and password
- Default user name: `Admin`
- Default user password: `webtex`

#### Initial setup of WebTeX
Follow initial setup instruction. Input berow text for each input form.
- User name: Your preferred user name
- User password: Your preferred user password
- JAVA_HOME: `/usr/lib/jvm/java-8-jdk`
- Absolute path of RedPen configuration file: `/home/user/redpen/conf/redpen-conf-en.xml`

#### Re-login to WebTeX, create working directory, write LaTeX document, and compile

