ARG E2XGRADER_VERSION=""
ARG FROM_REPO="false"
ARG E2XGRADER_BRANCH=""
ARG E2XGRADER_MODE=student
FROM $IMAGE_SOURCE

LABEL maintainer="e2x project H-BRS <e2x@inf.h-brs.de>"

USER $NB_USER

# Install e2xgrader
RUN if [ "$FROM_REPO" = "false" ]; then \
        if [ -z "$E2XGRADER_VERSION" ]; then \
            pip install e2xgrader; \
        else \
            pip install e2xgrader=="$E2XGRADER_VERSION"; \
        fi; \
    elif [ "$FROM_REPO" = "true" ]; then \
        pip install --no-cache-dir git+https://github.com/DigiKlausur/e2xgrader.git@"$E2XGRADER_BRANCH"; \
    fi

# Activate a mode
RUN e2xgrader activate $E2XGRADER_MODE --sys-prefix
