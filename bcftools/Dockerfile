# Note: the base image in Stage 1 represents the Debian version of the base image in Stage 2

# Stage 1
FROM debian:12.2-slim AS fuse-installer

RUN apt-get update && apt-get install -y fuse3

# Stage 2
FROM wave.seqera.io/wt/d8118d2a14ca/biocontainers/bcftools:1.20--h8b25389_0

COPY --from=fuse-installer /usr/bin/fusermount3 /usr/bin/fusermount3
RUN cd /usr/bin && ln -s fusermount3 fusermount
