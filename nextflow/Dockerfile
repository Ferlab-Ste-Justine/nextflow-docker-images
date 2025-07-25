# The container created from this image is used as a jump point within the
# kubernetes cluster to submit various ad-hoc jobs.

FROM nextflow/nextflow:24.10.5

# Adding a few command line utilities
# Note: gzip is required to access the nextflow pod via the vscode extension
RUN yum update -y && yum install -y --setopt=skip_missing_names_on_install=False \
nano-5.8-3.amzn2023.0.4.x86_64 \
vim-enhanced-2:9.1.785-1.amzn2023.0.1.x86_64 \
tar-2:1.34-1.amzn2023.0.4.x86_64 \
less-608-2.amzn2023.0.2.x86_64 \
wget-1.21.3-1.amzn2023.0.4.x86_64 \
unzip-6.0-57.amzn2023.0.2.x86_64 \
zip-3.0-28.amzn2023.0.2.x86_64 \
gzip-1.12-1.amzn2023.0.1.x86_64 \
awscli-2-2.17.18-1.amzn2023.0.1 \
&& yum clean all

RUN curl "https://downloads.rclone.org/v1.70.3/rclone-v1.70.3-linux-amd64.zip" -o "rclone.zip" && \
    unzip rclone.zip && \
    cp rclone-v1.70.3-linux-amd64/rclone /usr/local/bin/rclone && \
    rm -rf rclone-v1.70.3-linux-amd64 rclone.zip