FROM haskell:8.8.3-buster

RUN apt-get update \
    && apt-get install -y --no-install-recommends libicu-dev libncurses-dev libgmp-dev

RUN stack setup 8.8.3 \
    && stack install ghcid \
    && stack install hoogle


RUN cd /home \
    && git clone https://github.com/haskell/haskell-ide-engine --recurse-submodules \
    && cd haskell-ide-engine \
    && sed -i "s|lts-14.27 # last lts GHC 8.6.5|lts-15.7 # lts GHC 8.8.3|g" ./install/shake.yaml \
    && stack ./install.hs hie \
    && stack ./install.hs data