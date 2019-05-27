OS ubuntu 18 (It would be wrong on ubuntu 14, docker ce is no longer support 14 version)

1. install docker ce: (you will need refer the link for detail https://docs.docker.com/install/linux/docker-ce/ubuntu/)

    i. Uninstall old versions:

        sudo apt-get remove docker docker-engine

        docker.io containerd runc

    ii. Set up repository:

        sudo apt-get update

        sudo apt-get install \
        apt-transport-https \
        ca-certificates \
        curl \
        gnupg-agent \
        software-properties-common
        
        curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

        sudo add-apt-repository \
        "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
        $(lsb_release -cs) \
        stable"

    iii. Install docker ce

        sudo apt-get update

        sudo apt-get install docker-ce

        docker-ce-cli containerd.io

        make sure your verify your Docker CE is installed:
        sudo docker run hello-world

2. install docker-compose: link https://docs.docker.com/compose/install/
    
    sudo curl -L "https://github.com/docker/compose/releases/download/1.24.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

    sudo chmod +x /usr/local/bin/docker-compose

    Test your docker-compose:

        docker-compose --version

    if output is like this:
    docker-compose version 1.24.0, build 1110ad01
    you can go next.

3. Go to root folder and RUN:

Build containers:

    sudo docker-compose build

Up:

    sudo docker-compose up

    if there is something wrong relating to "Table 'profile' already exists". Run "sudo docker-compose up" again, it will be fine. Please let me know if it's still wrong.

4. Open your browser to check content "localhost:5000"

5. Setup data and start Nginx server:

    i. Run "docker ps -a" and find id of Image "app"

    ii. Run "docker exec -ti <id> bash to access container app

    iii. Run "python3 indeed_scrape.py" to update data for mysql. Please note that, you don't need to run it if db database built and run successfully in previous steps. Check it by "docker ps -a"

    iv. Run "service nginx start"

6. Check the website on browser with your IP


Jack (kazucuong@yahoo.com)

