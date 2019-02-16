Hướng dẫn cài đặt docker
====================================================

#I. Yêu cầu

  - Hệ điều hành: Linux (Ubuntu, CentoS)

  - Ram: Tối thiểu 2GB

  - Bộ nhớ tối thiểu: 10GB

  - 64 bit, Version kernel >= 3.1. Kiểm tra bằng lệnh: `uname -r`

#II. Cài đặt

  - `sudo apt-get update`

  - `sudo apt-get install apt-transport-https ca-certificates curl gnupg-agent software-properties-common`

  - `curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -`

  - `sudo apt-key fingerprint 0EBFCD88`

  - `sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"`

  - `sudo apt-get update`

  - `sudo apt-get install docker-ce docker-ce-cli containerd.io`

  - ``