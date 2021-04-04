FROM debian:10

RUN apt-get update && apt-get install -y vim curl html2text
WORKDIR /work
RUN curl -fsSLO  http://lfsbookja.osdn.jp/10.1-ja/chapter02/hostreqs.html
RUN html2text hostreqs.html | awk '/#!\/bin\/bash/,/EOF/' | sed -e '/EOF/d' > version-check.sh | chmod +x version-check.sh
RUN sh version-check.sh 2> not_found.log
#RUN awk -F ':' '{print $4}' not_found.log
RUN apt-get install -y binutils bison gawk gcc g++ make patch python3 texinfo
