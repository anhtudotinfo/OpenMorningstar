FROM ubuntu:latest 
LABEL maintainer="jeep.jipu@gmail.com" version="1.0"
ARG version=TShock4.5.12_Terraria1.4.3.2
WORKDIR /root

# 换源
# RUN mv /etc/apt/sources.list /etc/apt/sources.list.bak
# COPY ./_mirror_cn/aliyun-sources.list /etc/apt/sources.list
RUN apt update && apt upgrade -y

# 安装mono-devel
RUN apt install -y gnupg ca-certificates \
	&& apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 3FA7E0328081BFF6A14DA29AA6A19B38D3D831EF \
	&& "deb https://download.mono-project.com/repo/ubuntu stable-focal main" | tee /etc/apt/sources.list.d/mono-official-stable.list \
	&& apt update && apt install -y mono-devel

# 安装必要工具
RUN apt install -y unzip vim wget
# 安装tshock
RUN wget https://github.com/Pryaxis/TShock/releases/download/v4.5.12/${version}.zip -O /root/tshock.zip
# COPY tshock/tshock-release/${version}.zip /root/tshock.zip 
RUN unzip tshock.zip -d /root/TShock/ && rm tshock.zip

# 解决路径无法访问问题
RUN mkdir -p /root/.local/share/Terraria
RUN chmod 777 /root/.local/share/Terraria

COPY tshock/start.sh /start.sh
RUN chmod +x /start.sh
EXPOSE 7777





