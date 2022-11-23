FROM ubuntu:latest

RUN apt update && apt install  openssh-server sudo -y && apt-get install boxes --fix-missing -y && apt-get install figlet -y

RUN unset HISTFILE

RUN useradd -rm -d /home/challenge4 -s /bin/bash -u 1000 challenge4
RUN useradd -s /bin/bash -u 1002 flag
RUN useradd -s /bin/bash -u 1001 shine102 
# add shine102 to group flag
RUN usermod -aG flag shine102


RUN echo "figlet -f standard 'Challenge 4'| boxes -d scroll; echo 'Ai mới là chủ sở hữu thực sự?'" >> home/challenge4/.bashrc

RUN chown -R root:root /home/challenge4 

# copy material
COPY readme.md /home/challenge4/readme.md
COPY flag.txt /home/challenge4/flag.txt
COPY user.txt /home/challenge4/user.txt

RUN chmod 705 /home/challenge4

RUN chown flag:flag /home/challenge4/flag.txt
RUN chmod 740 /home/challenge4/flag.txt

RUN echo 'challenge4:EHC{W0lf_1n_4_fl0ck_0f_5h33p}' | chpasswd
RUN echo 'shine102:superidol' | chpasswd
RUN echo 'flag:fajlsdwqiceurwecoyniudfnewquyn' | chpasswd

RUN service ssh start

EXPOSE 22

CMD ["/usr/sbin/sshd","-D"]