FROM openjdk:8-jdk
VOLUME /config-repo
ENV JAVA_HOME              /usr/lib/jvm/java-8-openjdk-amd64
ENV JAVA_OPTS              ""
ENV PATH                   $PATH:$JAVA_HOME/bin
ENV TIME_ZONE              Europe/Budapest
ENV SPRING_PROFILES_ACTIVE test
#ENV TZ=$TIME_ZONE
#RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
#RUN dpkg-reconfigure -f noninteractive tzdata
WORKDIR /app
RUN mkdir config
ADD service-feign-0.0.1-SNAPSHOT.jar  service-feign.jar
COPY application.yml ./config/
COPY pom.properties /config-repo/
RUN ln -sf /dev/stdout /app/service-feign.log
EXPOSE 8765
CMD ["java", "-Djava.security.egd=file:/dev/./urandom", "-Dspring.config.location=./config/application.yml", "-Xms256m", "-Xmx512m", "-jar", "service-feign.jar"]；
