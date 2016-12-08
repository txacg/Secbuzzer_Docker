# Pull base image.
FROM java:8-jdk

COPY ./twittercrawler.jar /tmp/twittercrawler.jar
COPY ./properties.xml /tmp/properties.xml

WORKDIR $JAVA_HOME

RUN groupadd JAVA
RUN useradd JAVA -g JAVA -p java
RUN chmod +x /tmp/twittercrawler.jar
RUN chmod +x /tmp/properties.xml

WORKDIR /tmp

CMD ["java" , "-jar"  "/tmp/twittercrawler.jar"]



