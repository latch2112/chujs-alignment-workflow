# Dockerfile to build snpEff container images
#############################################

FROM openjdk:8-jdk

RUN apt-get update && apt-get install -y unzip wget

RUN wget http://sourceforge.net/projects/snpeff/files/snpEff_latest_core.zip
RUN unzip snpEff_latest_core.zip
RUN rm snpEff_latest_core.zip

RUN cp snpEff/snpEff.jar .
RUN cp snpEff/snpEff.config .
WORKDIR /snpEff
RUN java -jar snpEff.jar download -v GRCh38.86
ADD start.sh .
COPY start.sh /opt/snpeff/
ENTRYPOINT ["sh", "/opt/snpeff/start.sh"]
