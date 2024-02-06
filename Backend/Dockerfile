# Build stage 
# This is a maven image to build the java
FROM maven:3.8.6-amazoncorretto-17 AS myapp-build

# Setting up the working ENV
ENV MYAPP_HOME /opt/myapp
WORKDIR $MYAPP_HOME

# Copying the code inside the docker and building it
COPY pom.xml .
COPY src ./src
RUN mvn package -DskipTests

# Run
FROM amazoncorretto:17

# Setting up the working ENV
ENV MYAPP_HOME /opt/myapp
WORKDIR $MYAPP_HOME

# Taking the artifact from the last stage
COPY --from=myapp-build $MYAPP_HOME/target/*.jar $MYAPP_HOME/myapp.jar

# Specifies the default command to run when the container starts. It executes the Java application using the JAR file.
ENTRYPOINT java -jar myapp.jar
