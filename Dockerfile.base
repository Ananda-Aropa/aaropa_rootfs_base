FROM devuan/migrated:ceres-slim AS base

COPY template /
COPY packages /

RUN apt update && apt full-upgrade -y --allow-unauthenticated

# Install additional apt utils 
RUN apt install -y --allow-unauthenticated apt-transport-https ca-certificates

# Re-run apt update after install apt utils
RUN apt update

# Install package list
RUN grep -Ev '^#' /pkglist.cfg | xargs apt install -y --no-install-recommends --no-install-suggests --allow-unauthenticated

# Clean up cache & files
RUN apt clean && rm -rf /var/lib/apt/lists/*
RUN rm /*.cfg