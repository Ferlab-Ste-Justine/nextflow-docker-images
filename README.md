# nextflow-docker-images
A collection of docker images designed for use with nextflow pipelines.



## Images

### Nextflow
This docker image is designed to create long-running Nextflow pods. It includes nextflow and several command-line
utilities such as the AWS CLI and Rclone. Additionally, it provides more basic linux commands like tar, which are 
not included in the base nextflow image.

### BCFtools
This docker image is designed to represent BCFtools with the addition of having FUSE (specifically the `fusermount` binary) available to mount the Fusion filesystem.


## Local Testing Commands

Here are example commands for the Nextflow image. You can adapt these commands for other images as needed.

#### Building the Docker Image

To build it locally, you can use the following command from the project root directory:

```
docker build nextflow -t ferlabcrsj/nextflow:dev
```

#### Running the Docker Container
To open a shell on a docker container created from this image, run the following command:

```
docker run -it --rm ferlabcrsj/nextflow:dev /bin/bash
```


Since the `--rm` option is specified, the container will be automatically deleted once you exit the shell.

If you are using a different image, make sure to change the image tag (ferlabcrsj/nextflow:dev) accordingly.

#### Running trivy checks

```
trivy image --severity HIGH,CRITICAL --exit-code 1  --ignorefile nextflow/.trivyignore_image ferlabcrsj/nextflow:dev

trivy conf --severity 'HIGH,CRITICAL' nextflow --ignorefile nextflow/.trivyignore_config
```
