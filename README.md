## Dataiku DSS with Python3.x.x and R

### OSX and Linux

#### To build
After cloning the repository run `build.sh` or:

`docker build . -t dataiku/dss:python3_r`

#### To run
After building the image, `dataiku/dss:python3_r` run the container using `dataiku_run.sh` or by using:

`docker run -p 10000:10000 -v $(pwd)/dss:/home/dataiku/dss dataiku/dss:python3_r`

### Windows

#### To build
After cloning the repository run `build.sh` or:

`docker build . -t dataiku/dss:python3_r`

#### To run
After building the image, `dataiku/dss:python3_r` run it using the following commands:

- CMD
`docker run -p 10000:10000 -v %cd%/dss:/home/dataiku/dss dataiku/dss:python3_r`

- Powershell
`docker run -p 10000:10000 -v ${PWD}/dss:/home/dataiku/dss dataiku/dss:python3_r`
