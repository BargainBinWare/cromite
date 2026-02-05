ARG VERSION

FROM uazo/chromium:$VERSION

ARG CROMITE_SHA
ENV CROMITE_SHA=$CROMITE_SHA

ARG HTTP_PROXY
ENV HTTP_PROXY=$HTTP_PROXY
ENV HTTPS_PROXY=$HTTP_PROXY
ENV https_proxy=$HTTP_PROXY

#USER lg
WORKDIR /home/lg/working_dir

RUN sudo chown lg /etc/apt/apt.conf.d/proxy.conf
RUN sudo echo "Acquire::http::Proxy \"$HTTP_PROXY\";" >/etc/apt/apt.conf.d/proxy.conf
RUN sudo apt-get update

COPY tools/images/cromite-source/apply-cromite-patches.sh .
COPY . cromite/

RUN sudo chown -R lg:lg cromite && \
    sudo chmod +x ./apply-cromite-patches.sh

RUN ./apply-cromite-patches.sh

