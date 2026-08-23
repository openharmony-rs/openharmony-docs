# OpenHarmony Docker Image

### Docker Image

This document provides guidance on building the Docker image for mini- and small-system devices.

The Docker image of OpenHarmony is hosted on [HUAWEI Cloud SWR](https://auth.huaweicloud.com/authui/login.html?service=https%3A%2F%2Fconsole.huaweicloud.com%2Fswr%2F%3Fregion%3Dcn-north-4%26cloud_route_state%3D%2Fapp%2Fwarehouse%2FwarehouseMangeDetail%2Fci-service%2Fopenharmony-standard-build-env-22.04%3Ftype%3DownImage&locale=en-us#/login). Using the Docker image will help simplify environment configurations needed for the building. The following table lists container-based options needed for building in the standalone [Docker environment](https://gitcode.com/openharmony/docs/blob/master/en/device-dev/get-code/gettools-acquire.md).

| Docker Image Repository                                      | Tag     | Description                                               |
| :----------------------------------------------------------- | :------ | :-------------------------------------------------------- |
| `swr.cn-north-4.myhuaweicloud.com/ci-service/openharmony-standard-build-env-22.04` | `4.0.0` | The OpenHarmony build environment has been pre-installed. |

### Usage

 After downloading the OpenHarmony code, perform the steps below to access the Docker environment. 

1. Obtain the Docker image.
     ```shell
     docker pull swr.cn-north-4.myhuaweicloud.com/ci-service/openharmony-standard-build-env-22.04:4.0.0
     ```
2. Go to the root directory of OpenHarmony code and run the following command to access the Docker build environment:
     ```shell
     docker run -it -v $(pwd):/home/openharmony swr.cn-north-4.myhuaweicloud.com/ci-service/openharmony-standard-build-env-22.04:4.0.0
     ```
3. Run the following script to start building for different platforms.
     ```shell
     hb set # Press the Up or Down key to select the platform to build on, then press Enter.
     hb build -f # Start building.
     ```
