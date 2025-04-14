FROM opendjdk:11 as BUILD_IMAGE
RUN apt update && apt install maven -y 
RUN git clone https://github.com/gautamabhish/vprofile-project-practise.git
RUN cd vprofile-project-practise && git checkout docker && mvn install 

From tomcat:9-jre11 
RUN rm -rf /usr/local/tomct/webapps/*
COPY --from=BUILD_IMAGE vprofile-project-practise/target/vprofile-v2-war /usr/local/tomct/webapps/ROOT.war


EXPOSE 8080

CMD [ "catalina.sh" ,"run"]