from adoptopenjdk/openjdk11:alpine as build

run apk add curl bash vim unzip git
run curl https://downloads.apache.org/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.tar.gz -o mvn.tar.gz
run tar -xzf mvn.tar.gz

env M2_HOME=apache-maven-3.6.3
env JAVA_HOME=/opt/java/openjdk/
env PATH=$PATH:/$M2_HOME/bin

run git clone https://github.com/spring-petclinic/spring-petclinic-rest.git
run cd spring-petclinic-rest && \
    mvn clean install

from adoptopenjdk/openjdk11:alpine
copy --from=build /spring-petclinic-rest/target/spring-petclinic-rest-2.2.5.jar /
cmd ["java", "-jar", "spring-petclinic-rest-2.2.5.jar"]
