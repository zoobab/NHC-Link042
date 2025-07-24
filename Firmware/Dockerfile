FROM alpine:3.22 as build-stage
MAINTAINER Benjamin Henrion <zoobab@gmail.com>
LABEL Description="NHC-Link042, and stm32 firmware to flash ch32v003 chips"

RUN apk add build-base cmake gcc-arm-none-eabi newlib-arm-none-eabi

ADD . /nhc
WORKDIR /nhc

RUN cmake .
RUN make

FROM scratch AS export-stage
COPY --from=build-stage /nhc/bin/*.bin /
