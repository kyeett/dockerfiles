# docker run -it --rm -p 8888:8888 jupyter/scipy-notebook

# Use the scipy-notebook as base
FROM jupyter/scipy-notebook

USER root

# Install add-apt-repository (needed for apt-get install golang..)
RUN apt-get -y update
RUN apt-get -y install software-properties-common python-software-properties

# Install Golang
# https://github.com/golang/go/wiki/Ubuntu
RUN add-apt-repository ppa:gophers/archive
RUN apt-get update
RUN apt-get -y install golang-1.9-go

# Install ZeroMQ
RUN echo "deb http://download.opensuse.org/repositories/network:/messaging:/zeromq:/release-stable/Debian_9.0/ ./" >> /etc/apt/sources.list
RUN wget https://download.opensuse.org/repositories/network:/messaging:/zeromq:/release-stable/Debian_9.0/Release.key -O- | sudo apt-key add
RUN apt-get install libzmq3-dev

# export GOROOT=/usr/lib/go-1.9
# export PATH=$PATH:$GOROOT/bin
ENV GOROOT /usr/lib/go-1.9
ENV GOPATH /home/jovyan/go
RUN echo $PATH
RUN ls $GOROOT
ENV PATH $PATH:$GOROOT/bin:$GOPATH/bin
RUN echo $PATH

RUN go get -v github.com/gopherdata/gophernotes
RUN mkdir -p /home/jovyan/.local/share/jupyter/kernels/gophernotes
RUN cp $GOPATH/src/github.com/gopherdata/gophernotes/kernel/* /home/jovyan/.local/share/jupyter/kernels/gophernotes
RUN chown -R jovyan /home/jovyan

# Add additional kernels
RUN add-apt-repository ppa:chronitis/jupyter
RUN sudo apt-get update
RUN sudo apt-get -y install ihaskell

USER jovyan

