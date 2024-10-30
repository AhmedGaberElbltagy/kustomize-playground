# start sonar 
docker-compose up -d

# stop sonar 
docker-compose down

# access sonar
http://localhost:9000

# troubleshoot sonar 
docker-compose logs sonarqube

# sonar password 
root

# volumes 
Default Storage Location
By default, Docker stores named volumes in a specific directory on the host machine, typically:

Linux: /var/lib/docker/volumes/
macOS: Located in a hidden directory under ~/Library/Containers/com.docker.docker/Data/vms/0/ (specific to Docker Desktop).
Windows: Located in C:\ProgramData\Docker\volumes\ (specific to Docker Desktop).

# Accessing Volume Data 
docker volume ls
docker volume inspect <volume_name>
Example
If you defined a volume like sonarqube_data, you can inspect it:

docker volume inspect your_project_name_sonarqube_data