FROM clojure:openjdk-11-lein-buster

RUN apt-get update -qq
RUN apt-get install libquadmath0 -qq
WORKDIR /tmp
RUN wget http://archive.ubuntu.com/ubuntu/pool/universe/g/gcc-6/gcc-6-base_6.4.0-17ubuntu1_amd64.deb
RUN wget http://archive.ubuntu.com/ubuntu/pool/universe/g/gcc-6/libgfortran3_6.4.0-17ubuntu1_amd64.deb
RUN dpkg -i gcc-6-base_6.4.0-17ubuntu1_amd64.deb
RUN dpkg -i libgfortran3_6.4.0-17ubuntu1_amd64.deb

WORKDIR /usr/src/core.matrix

# Dependencies
COPY project.clj .
RUN lein deps

COPY . .
CMD ["/usr/local/bin/lein", "test"]
