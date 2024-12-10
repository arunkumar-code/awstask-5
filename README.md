# awstask-5
awstask-5
ec2 instance:
![image](https://github.com/user-attachments/assets/e167db39-acee-43cb-98a7-9e0441d0deb7)
taking source code from s3 bucket:
![image](https://github.com/user-attachments/assets/875d0b2e-1ae9-4700-8b8f-dab6c4668848)
deployment created for codedeploy:
![image](https://github.com/user-attachments/assets/a8274a7f-8565-4318-abfb-a9e1fb68bea2)
code pipeline:
![image](https://github.com/user-attachments/assets/b7f45e20-d4ae-459e-beed-bbedd23c4eca)
![image](https://github.com/user-attachments/assets/340bd6f9-1a63-4922-ba32-f2c1c01d85ae)
output:
![image](https://github.com/user-attachments/assets/2d014449-711e-4f1b-8a0e-052500e7dc45)


code: 
#!/bin/bash
sudo yum update -y
sudo yum install -y httpd

#!/bin/bash
sudo systemctl start httpd
sudo systemctl enable httpd

appspec.yml:
version: 0.0
os: linux
files:
  - source: index.html
    destination: /var/www/html
    overwrite: true
file_exists_behavior: OVERWRITE
hooks:
  AfterInstall:
    - location: httpd-install.sh
      timeout: 300
  ApplicationStart:
    - location: httpd-start.sh
      timeout: 300

IAM role:
![image](https://github.com/user-attachments/assets/81154aca-3b93-489d-ace8-3ce0441be9ff)

