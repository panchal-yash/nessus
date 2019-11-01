FROM centos:latest
MAINTAINER yashpanchal

RUN  yum update -y 
RUN yum install glibc zlib 
RUN NESSUS_VERSION="8.7.2"  
RUN DOWNLOAD_ID=$(curl -ssl -o - "https://www.tenable.com/downloads/nessus" | sed -n -e 's/.*data-download-id="\([0-9]*\)".*data-file-name="\([a-zA-Z0-9_\.-]\+\-es7\.x86_64\.rpm\).*".*/\1/p') 
RUN rpm --import https://static.tenable.com/marketing/RPM-GPG-KEY-Tenable 
RUN curl -o /tmp/Nessus-${NESSUS_VERSION}-es7.x86_64.rpm https://www.tenable.com/downloads/api/v1/public/pages/nessus/downloads/10085/download?i_agree_to_tenable_license_agreement=true  
RUN rpm -ivh /tmp/Nessus-${NESSUS_VERSION}-es7.x86_64.rpm 
EXPOSE 8834 443 25 53
ENTRYPOINT ["/opt/nessus/sbin/nessus-service"]
