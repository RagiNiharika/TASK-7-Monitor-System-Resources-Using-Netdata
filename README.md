 ## TASK 7: Monitor System Resources Using Netdata
## Objective
Install Netdata on an EC2 Ubuntu 22.04 server and visualize system & app performance metrics.

## Prerequisites
AWS account
Ubuntu 22.04 EC2 instance (t2.medium or higher recommended)
Security group: Allow inbound TCP 19999 (so you can access the Netdata dashboard in browser)
SSH access to EC2

 ## Installation Steps
1. Update system
sudo apt update && sudo apt upgrade -y

2. Install Docker
sudo apt install -y docker.io
sudo systemctl enable docker
sudo systemctl start docker

3. Run Netdata with Docker
sudo docker run -d --name=netdata \
  -p 19999:19999 \
  --cap-add SYS_PTRACE \
  --security-opt apparmor=unconfined \
  netdata/netdata

-d → run in background

--name=netdata → container name

-p 19999:19999 → expose Netdata UI

Extra flags → allow proper monitoring

## Access Dashboard
Open your browser:
http://<EC2-Public-IP>:19999
we should see Netdata dashboard with metrics like:
CPU Usage
Memory Usage
Disk I/O
Docker Container Metrics

## Logs

Check container logs if needed:
sudo docker logs -f netdata

## Container status:

sudo docker ps

## Outcome

Lightweight monitoring tool installed
Ability to visualize system & container performance
Basic knowledge of server monitoring with Netdata

Would you like me to write these steps as ready-to-run shell commands in order (so you can copy-paste directly), or do you prefer a GitHub-style README.md file you can upload with screenshots?

ChatGPT can make mis
