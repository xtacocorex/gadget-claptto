# BASE OFF MY GADGET CHIP IO CHIPTAINER
FROM xtacocorex/gadget-chip-io

# INSTALL THE THINGS
RUN apk update && \
    # CLAPTTO SPECIFIC PACKAGES
    apk add --no-cache gd && \
    apk add --no-cache gd-dev && \
    apk add --no-cache linux-headers && \
    apk add --no-cache gifsicle && \
    apk add --no-cache imagemagick && \
    # VU METER STUFF REQUIRED FOR CLAPTTO
    apk add --no-cache git && \
    apk add --no-cache gcc && \
    apk add --no-cache g++ && \
    apk add --no-cache gzip && \
    apk add --no-cache make && \
    apk add --no-cache alsa-lib-dev && \
    apk add --no-cache python-dev && \
    apk add --no-cache py2-pip && \
    pip install --upgrade pip && \
    pip install pyalsaaudio && \
    # FSWEBCAM INSTALL
    git clone https://github.com/fsphil/fswebcam.git && \
    cd fswebcam && \
    ./configure --prefix=/usr && \
    make && \
    make install && \
    cd ../ && rm -rf fswebcam && \
    # CLAPTTO INSTALL
    git clone https://github.com/xtacocorex/claptto.git && \
    cd claptto && \
    cp claptto.py / && \
    cd ../ && rm -rf claptto && \
    # Remove unneeded packages once build is complete.
    apk del git && \
    apk del gcc && \
    apk del g++ && \
    apk del make && \
    apk del py2-pip && \
    apk del linux-headers && \
    apk del gd-dev && \
    apk del gzip && \
    apk del python-dev && \
    # REMOVE CACHE
    rm -rf /var/cache/apk/*

# THE ENTRY POINT
ENTRYPOINT echo "CLAPTTO IS STARTING" && \
    python claptto.py

