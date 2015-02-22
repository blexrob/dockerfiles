# Base docker image
FROM debian:jessie
MAINTAINER Jessica Frazelle <jess@docker.com>

RUN rm -rf /var/lib/apt/lists/

# Install Chromium
RUN sed -i.bak 's/jessie main/jessie main contrib non-free/g' /etc/apt/sources.list && \
    cat /etc/apt/sources.list && \
    mkdir -p /usr/share/icons/hicolor && \
    apt-get update && apt-get install -y \
    ca-certificates \
    gconf-service \
    libappindicator1 \
    libasound2 \
    libcanberra-gtk-module \
    libcurl3 \
    libexif-dev \
    libgconf-2-4 \
    libnspr4 \
    libnss3 \
    libpango1.0-0 \
    libv4l-0 \
    libxss1 \
    libxtst6 \
    wget \
    xdg-utils \
    apt-transport-https \
    --no-install-recommends && \
    wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add - && \
    sh -c 'echo "deb https://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google-chrome.list' && \
    apt-get update && \
    apt-get install -y google-chrome-unstable && \
    apt-get install -y pepperflashplugin-nonfree --no-install-recommends

COPY local.conf /etc/fonts/local.conf

CMD ["/usr/bin/google-chrome-unstable", "--no-sandbox", "--user-data-dir=/data"]