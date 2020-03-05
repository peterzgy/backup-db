# backup databases
  Only support postgres right now

  ```
  # build docker and run
  docker build . -t backup-db
  docker run -d backup-db
  ```
  client
  ```
  docker run -d \
  --name backup-test \
  -e backup_server_ip=192.168.1.76 \
  -e backup_server_port=9977 \
  -e backup_project_name=test \
  -e backup_command="pg_dump -a \"host=192.168.1.11 port=5433 user=postgres password=password dbname=test\"" \
  -e max_save_days=30 \
  -e notice_email=277172506@qq.com \
  backup-test
  ```
  
  server
  ```
  docker run -d \
  --name backup-server \
  -e backup_server_ip= \
  -e backup_server_port=9977 \
  -e backup_project_name=test \
  -e backup_command= \
  -e max_save_days=30 \
  -e notice_email=277172506@qq.com \
  backup-server
  ```