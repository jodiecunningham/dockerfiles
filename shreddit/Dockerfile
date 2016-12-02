#DESCRIPTION: Run x89/Shreddit in a container
#AUTHOR: Jodie Cunningham
#USAGE:
#	# Build image
#	docker built -t shreddit .
#
#	# Run the container with your config file
#	docker run -v $HOME/shreddit.yml:/home/shredditUser/shreddit.yml shreddit
#
#

FROM alpine:3.3
MAINTAINER Jodie Cunningham <jodie.cunningham@gmail.com>

RUN apk update
RUN apk add python git openssl

RUN cd /root && wget "https://bootstrap.pypa.io/get-pip.py" && python get-pip.py

RUN git clone https://github.com/x89/Shreddit.git  &&  cd Shreddit && pip install -r requirements.txt && python setup.py install

RUN adduser -s `which nologin` -g '' -h /home/shredditUser -D shredditUser

USER shredditUser
ENTRYPOINT ["shreddit","-c","/home/shredditUser/shreddit.yml"]
