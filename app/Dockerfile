FROM python:3
MAINTAINER Birgir Hrafn <birgir@datasmoothie.io>

# When you wan't to FORCE the docker image to refresh the cache
ENV REFRESHED_AT 2018-04-03

RUN apt-get update -y \
  && apt-get install -y build-essential\
                        python3\
                        python3-pip

# Disable Django output buffers. (Make it respond immidately)
ENV PYTHONUNBUFFERED 1

# The folders must exist to be able to mount the volumes
RUN mkdir /src

ADD ./requirements.txt /requirements.txt
ADD ./pystartup /pystartup

# If you change the requirements.txt file, then update REFRESHED_AT
ENV PIP_UPDATED_AT 2018-06-20
RUN pip install -r /requirements.txt
RUN pip install certifi

ENV PYTHONWARNINGS "ignore:Unverified HTTPS request"
ENV PYTHONSTARTUP=/pystartupd
