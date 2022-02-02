root@u-45755:/home/user/Docker# docker run -d -p 127.0.0.1:8892:80 --name rbm-dkr-06-local --log-driver local --log-opt max-size=10m nginx:stable 
 
root@u-45755:/home/user/Docker# docker ps  
CONTAINER ID   IMAGE          COMMAND                  CREATED         STATUS          PORTS                    NAMES 
edcf49b57a8d   nginx:stable   "/docker-entrypoint.…"   10 minutes ago    Up 10 minutes   127.0.0.1:8892->80/tcp   rbm-dkr-06-local 
 
root@u-45755:/home/user/Docker# curl --silent http://127.0.0.1:8892 > /dev/null 

root@u-45755:/home/user/Docker# cat /var/lib/docker/containers/edcf49b57a8d60254ef16da9d19c54fce25a57cc980e08ce645639a6cb22c649/local-logs/container.log 
``
stdout���������`/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configurationt]
stdout���������I/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/]i
stdout���������U/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.shiq
stdout�ـ�����]10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.confqs
stdout蛕������_10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.confse
stdout�󝃯����Q/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.shee
stdout���������Q/docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sheU
stdout�������A/docker-entrypoint.sh: Configuration complete; ready for start upUT
stderr���������@2022/01/31 17:18:53 [notice] 1#1: using the "epoll" event methodTB
stderr���������.2022/01/31 17:18:53 [notice] 1#1: nginx/1.20.2Be
stderrȝ�������Q2022/01/31 17:18:53 [notice] 1#1: built by gcc 10.2.1 20210110 (Debian 10.2.1-6) eQ
stderr��������=2022/01/31 17:18:53 [notice] 1#1: OS: Linux 5.13.0-27-genericQ_
stderr���������K2022/01/31 17:18:53 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1048576:1048576_L
stderr���������82022/01/31 17:18:53 [notice] 1#1: start worker processesLM
stderr�采�����92022/01/31 17:18:53 [notice] 1#1: start worker process 31MM
stderr���������92022/01/31 17:18:53 [notice] 1#1: start worker process 32MM
stderr毒������92022/01/31 17:18:53 [notice] 1#1: start worker process 33MM
stderr䓶������92022/01/31 17:18:53 [notice] 1#1: start worker process 34Mn
stdout�坫�����Z172.17.0.1 - - [31/Jan/2022:17:19:17 +0000] "GET / HTTP/1.1" 200 612 "-" "curl/7.68.0" "-"n` 
`` 
 
daemon json file [here](https://github.com/uladzimarkov/docker-6/blob/main/daemon.json) 
 
root@u-45755:/home/user/Docker# docker run -d -p 127.0.0.1:8893:80 --name rbm-dkr-06-global  nginx:stable 
 
root@u-45755:/home/user/Docker# curl --silent http://127.0.0.1:8893 > /dev/null 
 
root@u-45755:/home/user/Docker# cat /var/lib/docker/containers/1e8a54b49ecb8696d845918a32c55165df7ec0fe6957807b281c938b0fb8eae6/1e8a54b49ecb8696d845918a32c55165df7ec0fe6957807b281c938b0fb8eae6-json.log  
``
{"log":"/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration\n","stream":"stdout","time":"2022-02-02T10:26:39.918059428Z"}
{"log":"/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/\n","stream":"stdout","time":"2022-02-02T10:26:39.91808685Z"}
{"log":"/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh\n","stream":"stdout","time":"2022-02-02T10:26:39.919361781Z"}
{"log":"10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf\n","stream":"stdout","time":"2022-02-02T10:26:39.930465467Z"}
{"log":"10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf\n","stream":"stdout","time":"2022-02-02T10:26:39.939915456Z"}
{"log":"/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh\n","stream":"stdout","time":"2022-02-02T10:26:39.940097292Z"}
{"log":"/docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh\n","stream":"stdout","time":"2022-02-02T10:26:39.94308091Z"}
{"log":"/docker-entrypoint.sh: Configuration complete; ready for start up\n","stream":"stdout","time":"2022-02-02T10:26:39.944599446Z"}
{"log":"2022/02/02 10:26:39 [notice] 1#1: using the \"epoll\" event method\n","stream":"stderr","time":"2022-02-02T10:26:39.94999531Z"}
{"log":"2022/02/02 10:26:39 [notice] 1#1: nginx/1.20.2\n","stream":"stderr","time":"2022-02-02T10:26:39.950009805Z"}
{"log":"2022/02/02 10:26:39 [notice] 1#1: built by gcc 10.2.1 20210110 (Debian 10.2.1-6) \n","stream":"stderr","time":"2022-02-02T10:26:39.950013615Z"}
{"log":"2022/02/02 10:26:39 [notice] 1#1: OS: Linux 5.13.0-27-generic\n","stream":"stderr","time":"2022-02-02T10:26:39.950017057Z"}
{"log":"2022/02/02 10:26:39 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1048576:1048576\n","stream":"stderr","time":"2022-02-02T10:26:39.950020338Z"}
{"log":"2022/02/02 10:26:39 [notice] 1#1: start worker processes\n","stream":"stderr","time":"2022-02-02T10:26:39.950050565Z"}
{"log":"2022/02/02 10:26:39 [notice] 1#1: start worker process 33\n","stream":"stderr","time":"2022-02-02T10:26:39.950157467Z"}
{"log":"2022/02/02 10:26:39 [notice] 1#1: start worker process 34\n","stream":"stderr","time":"2022-02-02T10:26:39.950265596Z"}
{"log":"2022/02/02 10:26:39 [notice] 1#1: start worker process 35\n","stream":"stderr","time":"2022-02-02T10:26:39.950373484Z"}
{"log":"2022/02/02 10:26:39 [notice] 1#1: start worker process 36\n","stream":"stderr","time":"2022-02-02T10:26:39.950495963Z"}
{"log":"172.17.0.1 - - [02/Feb/2022:10:27:01 +0000] \"GET / HTTP/1.1\" 200 612 \"-\" \"curl/7.68.0\" \"-\"\n","stream":"stdout","time":"2022-02-02T10:27:01.655149348Z"}
``
