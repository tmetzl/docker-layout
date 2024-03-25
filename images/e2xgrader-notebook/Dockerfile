ARG E2XGRADER_VERSION=""
ARG FROM_REPO="false"
ARG E2XGRADER_BRANCH=""
FROM $IMAGE_SOURCE
# Inherit from any image, then just install e2xgrader
LABEL maintainer="e2x project H-BRS <e2x@inf.h-brs.de>"

USER $NB_USER

# Install from PyPi
RUN if [ "$E2XGRADER_VERSION" == "" ] && [ "$FROM_REPO" == "false"]; then \
        pip install e2xgrader
    elif [ "$FROM_REPO" == "false"]; then \
        pip install e2xgrader=="$E2XGRADER_VERSION"
    fi

# Install from source
RUN if [ "$FROM_REPO" == "true"]; then \
        pip install --no-cache-dir git+https://github.com/DigiKlausur/e2xgrader.git@$E2XGRADER_BRANCH
    fi
