FROM microsoft/dotnet:latest

#docker Section
RUN apt-get update -y

RUN apt-get -y install \
     apt-transport-https \
     ca-certificates \
     curl \
     software-properties-common
	 
RUN curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add -

RUN add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/debian \
   $(lsb_release -cs) \
   stable"	
   
RUN apt-get update

RUN apt-get -y install docker-ce

RUN apt-get update
#MONO Section
RUN apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 3FA7E0328081BFF6A14DA29AA6A19B38D3D831EF \
	&& echo "deb http://download.mono-project.com/repo/debian wheezy-libjpeg62-compat main" | tee -a /etc/apt/sources.list.d/mono-xamarin.list \
	&& echo "deb http://download.mono-project.com/repo/debian wheezy/snapshots/4.4.2.11 main" | tee -a /etc/apt/sources.list.d/mono-xamarin.list \
	&& apt-get update \
	&& apt-get install -y mono-devel ca-certificates-mono fsharp mono-vbnc nuget referenceassemblies-pcl \
	&& rm -rf /var/lib/apt/lists/*
	
COPY docker-entrypoint.sh .

ENTRYPOINT ["sh", "docker-entrypoint.sh"]

#COPY docker-entrypoint.sh /usr/local/bin/

#ENTRYPOINT ["docker-entrypoint.sh"]
#CMD ["sh"]