#=============================================================================#
# File Name:      Makefile
# Author:         Edward J. Sabol
# Creation Date:  2020/04/27
# Project:        HEASARC :: SciServer
#=============================================================================#
# File Description:
#   Used for building HEASoft + CIAO Docker image for SciServer.
#=============================================================================#
# High Energy Astrophysics Science Archive Research Center (HEASARC),
# NASA's Goddard Space Flight Center, Greenbelt, MD 20771, USA.
#
# You are free to use this code as you wish, but unless you change
# it significantly, please leave the above name and address intact.
#=============================================================================#

IMAGE_NAME = heasarc
IMAGE_VERSION = 6.29
IMAGE_LABEL = v$(IMAGE_VERSION)

image:
	@echo "Building Docker image ${IMAGE_NAME}:${IMAGE_LABEL}..."
	docker build --no-cache --network=host -t $(IMAGE_NAME):$(IMAGE_LABEL) .
	-(docker images -q -f dangling=true | xargs docker rmi)

latest: image
	@echo "Tagging Docker image ${IMAGE_NAME}:${IMAGE_LABEL} with latest..."
	docker tag $(IMAGE_NAME):$(IMAGE_LABEL) $(IMAGE_NAME):latest
	-(docker images -q -f dangling=true | xargs docker rmi)
