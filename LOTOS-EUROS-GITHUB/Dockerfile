FROM ubuntu:22.04

RUN apt-get update && apt-get install -y \
    build-essential gfortran openmpi-bin libopenmpi-dev \
    libnetcdf-dev libnetcdff-dev \
    udunits-bin libudunits2-dev \
    wget curl git make

ENV MPIFC=gfortran \
    OMPI_FC=gfortran \
    NEW_BUILD=1 \
    MPI_HOME=/usr \
    PATH=/usr/bin:$PATH \
    LD_LIBRARY_PATH=/usr/lib:$LD_LIBRARY_PATH \
    CPATH=/usr/include:$CPATH \
    LIBRARY_PATH=/usr/lib:$LIBRARY_PATH

WORKDIR /opt/LE
COPY ./openle-master/v2.3.000 ./v2.3.000
WORKDIR /opt/LE/v2.3.000
RUN ./base/000/bin/setup-le -n proj/myproj/000/rc/lotos-euros.rc

ENTRYPOINT ["./base/000/bin/lotos-euros", "-n", "proj/myproj/000/rc/lotos-euros.rc"]
