FROM ubuntu:20.04

LABEL maintainer="VzdornovNA88@yandex.com"

RUN useradd -ms /bin/bash vscode-user

RUN dpkg --add-architecture i386

RUN apt update

RUN apt install -y wget 
RUN apt install -y unzip

RUN apt install -y usbutils
RUN apt install -y usbutils:i386
RUN apt install -y libncurses5

RUN apt install -y make
RUN apt install -y cmake

RUN apt install -y git

RUN apt install -y stlink-tools

RUN mkdir opt/stm32-gcc-cmake-tool-chain

RUN wget https://github.com/VzdornovNA88/stm32-cmake/archive/refs/heads/master.zip -O stm32-cmake.zip
RUN unzip stm32-cmake.zip -d opt/stm32-gcc-cmake-tool-chain
RUN mv opt/stm32-gcc-cmake-tool-chain/stm32-cmake-master opt/stm32-gcc-cmake-tool-chain/stm32-cmake
RUN rm stm32-cmake.zip

RUN wget https://developer.arm.com/-/media/Files/downloads/gnu-rm/10-2020q4/gcc-arm-none-eabi-10-2020-q4-major-x86_64-linux.tar.bz2 -O gcc-arm-none-eabi.tar.bz2
RUN mkdir opt/stm32-gcc-cmake-tool-chain/eabi && tar xjfv gcc-arm-none-eabi.tar.bz2 -C opt/stm32-gcc-cmake-tool-chain/eabi --strip-components 1
RUN rm gcc-arm-none-eabi.tar.bz2

RUN wget https://github.com/posborne/cmsis-svd/archive/refs/tags/python-0.4.tar.gz -O cmsis-svd.tar.gz
RUN mkdir opt/stm32-gcc-cmake-tool-chain/cmsis-svd && tar xzfv cmsis-svd.tar.gz -C opt/stm32-gcc-cmake-tool-chain/cmsis-svd --strip-components 1
RUN rm cmsis-svd.tar.gz

RUN wget https://github.com/xpack-dev-tools/openocd-xpack/releases/download/v0.11.0-1/xpack-openocd-0.11.0-1-linux-x64.tar.gz -O OpenOCD.tar.gz
RUN mkdir opt/stm32-gcc-cmake-tool-chain/OpenOCD && tar xzfv OpenOCD.tar.gz -C opt/stm32-gcc-cmake-tool-chain/OpenOCD --strip-components 1
RUN rm OpenOCD.tar.gz

RUN wget https://github.com/STMicroelectronics/STM32CubeG4/archive/refs/tags/v1.3.0.tar.gz -O STM32CubeG4.tar.gz
RUN mkdir opt/stm32-gcc-cmake-tool-chain/STM32CubeG4 && tar xzfv STM32CubeG4.tar.gz -C opt/stm32-gcc-cmake-tool-chain/STM32CubeG4 --strip-components 1
RUN rm STM32CubeG4.tar.gz

ENV PATH="/opt/stm32-gcc-cmake-tool-chain/eabi/bin:/opt/stm32-gcc-cmake-tool-chain/OpenOCD/bin:${PATH}"
ENV CMAKE_NONE_EABI_STM32_TOOL_CHAIN="/opt/stm32-gcc-cmake-tool-chain"