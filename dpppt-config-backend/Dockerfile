FROM ubuntu

# Install maven
RUN apt-get -y update  && apt-get install default-jre default-jdk openjdk-11-jdk  maven -y

WORKDIR /code

# Prepare by downloading dependencies
ADD pom.xml /code/pom.xml

# Adding source, compile and package into a fat jar
ADD src /code/src
RUN ls -a
#RUN ["mvn", "install"]
#RUN mvn install -DskipTests
#RUN mvn install -Dmaven.test.skip=true
RUN mvn install -DskipTests
RUN ls -a target
EXPOSE 8080
#CMD ["java","-Dspring.profiles.active=dev","-jar","target/dpppt-config-backend-1.0.0-SNAPSHOT.jar"]
#CMD ["java","-jar","target/dpppt-config-backend-1.0.0-SNAPSHOT.jar","-Dspring.profiles.active=dev"]

CMD ["java","-jar","target/dpppt-config-backend.jar","-jar ","-Dspring.profiles.active=cloud-dev"]

