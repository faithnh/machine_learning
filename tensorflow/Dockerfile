FROM tensorflow/tensorflow:0.12.1-gpu

RUN apt-get update

RUN apt-get install -y git

# cloud9のインストール
RUN git clone https://github.com/c9/core.git /cloud9 && \
    cd /cloud9 && ./scripts/install-sdk.sh

RUN apt-get install -y nodejs

RUN update-alternatives --install /usr/bin/node node /usr/bin/nodejs 10

# cloud9がLD_LIBRARY_PATHを書き換えてnvidia系のものが動かなくしていたため
RUN echo -n "export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/nvidia/lib:/usr/local/nvidia/lib64:" >> /root/.bashrc

RUN pip install pandas git+https://github.com/tflearn/tflearn.git@0.2.2 h5py 

CMD ["node","/cloud9/server.js","--port","3000","--listen","0.0.0.0","-w","/share","--auth","auth:password"]
