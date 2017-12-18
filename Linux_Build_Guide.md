# Lunux Build Guide

## 1. Tools & Sources

* sudo apt-get update 
* sudo apt-get install curl build-essential libcurl4-openssl-dev git cmake pkg-config libssl-dev uuid-dev valgrind
* libglib2.0-dev libtool autoconf
* git clone https://github.com/KlipskCorp/iot-edge

## 2. Java (Oracle)

* sudo apt-get install software-properties-common
* sudo add-apt-repository ppa:webupd8team/java
* sudo apt-get update
* sudo apt-get install oracle-java8-installer
* export JAVA_HOME=/usr/lib/jvm/java-8-oracle (should be declared in .profile / .bashrc)

## 3. Maven

* sudo apt-get update
* sudo apt-get install maven

## 4. Installing CMake 3.x

* sudo apt-get remove cmake cmake-data
* sudo -E add-apt-repository -y ppa:george-edison55/cmake-3.x
* sudo -E apt-get update
* sudo apt-get install cmake

## 5. Build IOT-Edge Java Gateway library (might be skipped)

* cd /iot-edge/v1/bindings/java/gateway-java-binding
* mvn clean install

## 6. Compiling Samples (might be skipped)

* cd /iot-edge/v1/samples/java_sample/java_modules/Printer
* mvn clean install
* cd /iot-edge/v1/samples/java_sample/java_modules/Sensor
* mvn clean install

## 7. Compiling IoT Edge project for Java ( "--enable-java-binding" do the same as step 5 )

* /iot-edge/v1/tools/build.sh --enable-java-binding

## 8. Run samples (only with step 6)
* cd /iot-edge/v1/build/samples/java_sample/
* ./java_sample ../../../samples/java_sample/src/java_sample_lin.json

## 9. Run Java Gateway
* cd /iot-edge/v1/build/modules/java_gw/
* .java_gw <path_to_json_configuration>

NOTICE : **java_gw** module is a custom module that not included to iot-edge original repository. This module starts IoT-Edge Gateway on JVM and build modules by IoT Edge JSON Configuration
