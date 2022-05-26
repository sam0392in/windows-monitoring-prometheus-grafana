# Setup Windows Monitoring with Prometheus & Grafana

![alt text](./img.png?raw=true)


## Prerequisites
- Docker Desktop Running.
- Docker compose installed.

## Steps

1. Download windows exporter MSI and run using admin rights.
URL https://github.com/prometheus-community/windows_exporter/releases

2. Get IP Address of computer by ipconfig. (IPv4)
```
Ethernet adapter vEthernet (WSL):

   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . : fe80::74aa:c25f:7e02:4034%97
   IPv4 Address. . . . . . . . . . . : 172.23.92.1
   Subnet Mask . . . . . . . . . . . : 255.255.240.0
   Default Gateway . . . . . . . . . :

```
3. Check if the windows exporter is functional by running http://172.23.92.1:9182/ in browser. It should show windows_exporter metrics exposed at port 9182.

4. Update prometheus.yml line 30 and add the above URL of windows_exporter to add the target.

5. Create 2 directories named prometheus-data and grafana-data for data persistance.

6. check the files are present in same directory. 
```

-rw-r--r-- 1 sam03 197609    1436 May 26 20:00 README.md
-rw-r--r-- 1 sam03 197609     745 May 26 20:13 docker-compose.yml
drwxr-xr-x 1 sam03 197609       0 May 26 20:14 grafana-data/
-rw-r--r-- 1 sam03 197609     173 May 26 15:32 grafana-datasource.yml
-rw-r--r-- 1 sam03 197609   49567 May 26 14:45 grafana.ini
drwxr-xr-x 1 sam03 197609       0 May 26 20:13 prometheus-data/
-rw-r--r-- 1 sam03 197609     613 May 26 15:21 prometheus.yml
-rw-r--r-- 1 sam03 197609   68857 May 26 17:09 windows-grafana-dashboard.json
-rw-r--r-- 1 sam03 197609 9170944 May 26 15:08 windows_exporter-0.18.1-386.msi

```

7. update grafana username and password in grafana.ini line 248.

8. Make docker compose up by command
```

docker-compose up

```

9. Check if both the containers are up and running by 
```

docker-compose ps

```

10. Go to browser and open grafana by localhost:3000

11. Import dashboard JSON given present in current directory.

12. Save dashboard and monitor it.
