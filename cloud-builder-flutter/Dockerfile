# Flutter (https://flutter.io) Developement Environment for Linux
# ===============================================================
#
# This environment passes all Linux Flutter Doctor checks and is sufficient
# for building Android applications and running Flutter tests.
#
# To build iOS applications, a Mac development environment is necessary.
#

FROM debian:stretch

# Install Dependencies.
RUN apt update -y
RUN apt install -y \
  git \
  wget \
  curl \
  unzip \
  lib32stdc++6 \
  libglu1-mesa \
  default-jdk-headless

# Install Flutter.
ENV FLUTTER_ROOT="/opt/flutter"
RUN git clone https://github.com/flutter/flutter "${FLUTTER_ROOT}"
ENV PATH="${FLUTTER_ROOT}/bin:${PATH}"

# Disable analytics and crash reporting on the builder.
RUN flutter config --no-analytics

# Perform an artifact precache so that no extra assets need to be downloaded on demand.
RUN flutter precache

# Perform a doctor run.
RUN flutter doctor -v

# Switch to the correct channel
ARG channel=stable
RUN flutter channel $channel

# Perform a flutter upgrade
RUN flutter upgrade

ENTRYPOINT [ "flutter" ]
