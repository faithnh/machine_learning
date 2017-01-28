FROM tensorflow/tensorflow:0.12.1-gpu

RUN apt-get update

RUN apt-get install -y git

RUN git clone https://github.com/c9/core.git /cloud9 && \
    cd /cloud9 && ./scripts/install-sdk.sh

RUN apt-get install -y nodejs

RUN update-alternatives --install /usr/bin/node node /usr/bin/nodejs 10

CMD ["node","/cloud9/server.js","--port","3000","--listen","0.0.0.0","-w","/share","--auth","auth:password"]
