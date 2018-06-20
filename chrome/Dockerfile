FROM debian:sid

RUN apt-get update && apt-get install -y --no-install-recommends \
	apt-transport-https \
	ca-certificates \
	curl \
	gnupg

RUN curl -sSL https://dl.google.com/linux/linux_signing_key.pub | apt-key add - \
	&& echo "deb [arch=amd64] https://dl.google.com/linux/chrome/deb/ stable main" > /etc/apt/sources.list.d/google.list \
	&& apt-get update && apt-get install -y --no-install-recommends \
	google-chrome-stable

RUN groupadd -r chrome && useradd -r -g chrome -G audio,video chrome \
	&& mkdir -p /home/chrome/Downloads && chown -R chrome:chrome /home/chrome 

USER chrome

ENTRYPOINT ["google-chrome"]

