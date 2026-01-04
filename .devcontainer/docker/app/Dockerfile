# debian
FROM node:24.12.0-bookworm-slim

# install packages
RUN apt-get update && apt-get install -y --no-install-recommends \
    tzdata \
    ca-certificates \
    curl \
    unzip \
    git \
    chromium \
    fonts-ipafont-gothic \
    fonts-ipafont-mincho \
    fonts-noto-cjk \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# set chromium path for marp
ENV CHROME_PATH=/usr/bin/chromium

# install marp cli
RUN npm install -g @marp-team/marp-cli@4.2.3

# timezone
RUN ln -sf /usr/share/zoneinfo/Asia/Tokyo /etc/localtime
