**This readme file will explain deployment of ciso-app deployment on the local machine (RHEL-9)**
</br>
** STEP-1 ** </br>

clone the repo: </br>

**git clone https://github.com/intuitem/ciso-assistant-community.git**</br>

run the preparation script and follow the instructions:</br>

**./docker-compose.sh **</br>


** STEP-2 **</br>

- To fix x509 error (self-signed cert used by caddy ) while pulling docker images inside container </br>
  temporary solution</br>
  **export NODE_TLS_REJECT_UNAUTHORIZED=0**  </br>

- To fix on your host machine</br>
 
  **sudo cp /path/to/caddy_data/pki/authorities/local/root.crt  /etc/pki/ca-trust/source/anchors/**</br>
  **sudo update-ca-trust extract** </br>

- To fix port issues if already in use error </br>
  
  **netstat -nltup | grep <8443></br>**
  **sudo lsof -i : <8443></br>**
  **kill -9 <PID></br>**
  
** output**

![Image](https://github.com/user-attachments/assets/b39ea0dc-b423-4610-8e1c-f357bdf710ad)
  
