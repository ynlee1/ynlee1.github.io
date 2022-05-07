---
published: true
title: "How to install docker"
last_modified_at: 2022-05-08
categories:
  - docker
tags:
  - docker
---

## 최소 사양
* Linux Kernel 3.10
* Ubuntu 18.04, 20.04 (2021년 4월 30일 이후로 Ubuntu 16.04 LTS는 지원 종료)
* 64bit OS
<br><br>

## Install
1. Update 및 HTTP package 설치
    ```sh 
    sudo apt update 
    ```
    ```sh
    sudo apt-get install -y ca-certificates curl software-properties-common gnupg lsb-release
    ```

2. GPG Key 및 저장소 추가
    ```sh
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
    ```
   - GPG
     - GNU Privacy Guard(GnuPG)의 줄임말로서 배포 파일의 인증을 확인하는데 사용되는 자유 소프트웨어 패키지
     - RSA같은 공개 키 암호화 방식<br><br>

3. Docker Engine 설치
    ```sh
    curl -fsSL https://get.docker.com/ | sudo sh
    ```
     - 자동 설치 script<br><br>
4. Docker Version 확인
    ```sh
    sudo docker version
    ```
    <br><br>


## Run docker without sudo permission
1. Create Docker group
    ```sh
    sudo groupadd docker
    ```

2. Add user to docker group
    1. Method 1
        ```sh
        sudo usermod -aG docker ${USER}
        ```
    2. Method 2
        ```sh
        sudo gpasswd -a $USER docker
        ```

3. Restart docker
    ```sh
    sudo service docker restart
    ```

4. Re-login current user
    ```sh
    sudo su -    // Change as root
    su - [current user] // Change as current user
    ```
    <br><br>