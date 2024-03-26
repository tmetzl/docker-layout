ARG IMAGE_SOURCE=ghcr.io/digiklausur/docker-stacks/minimal-notebook:latest
FROM $IMAGE_SOURCE

ARG FROM_REPO=false
ARG E2XGRADER_VERSION=""
ARG E2XGRADER_BRANCH=""
ARG E2XGRADER_MODE=student

# Inherit from any image, then just install e2xgrader and activate a mode
LABEL maintainer="e2x project H-BRS <e2x@inf.h-brs.de>"

USER $NB_USER

# Install e2xgrader
RUN if [ "$FROM_REPO" = "false" ] && [ -z "$E2XGRADER_VERSION" ]; then \
        echo "Installing e2xgrader from default source..."; \
        pip install e2xgrader; \
    elif [ "$FROM_REPO" = "false" ] && [ -n "$E2XGRADER_VERSION" ]; then \
        echo "Installing e2xgrader version: $E2XGRADER_VERSION from PyPI..."; \
        pip install e2xgrader=="$E2XGRADER_VERSION"; \
    elif [ "$FROM_REPO" = "true" ]; then \
        echo "Installing e2xgrader from GitHub repository: https://github.com/DigiKlausur/e2xgrader.git@$E2XGRADER_BRANCH"; \
        pip install --no-cache-dir git+https://github.com/DigiKlausur/e2xgrader.git@"${E2XGRADER_BRANCH}"; \
    fi

# Activate a mode
RUN e2xgrader activate $E2XGRADER_MODE --sys-prefix
