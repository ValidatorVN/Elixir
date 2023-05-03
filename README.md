# Elixir

Cấu hình khuyến nghị:

    2CPU
    4GB RAM
    30GB SSD
    
Tạo VPS với chi phí $5, được tặng $200 trải nghiệm trong 60 ngày:

     https://bit.ly/DigitalOcean200 
     Video hướng dẫn: https://youtu.be/IdofxspCOQk
     
Đăng nhập vào VPS bằng lệnh:

    ssh root@<địa chỉ IP VPS>
    
    nhập password lúc khởi tạo VPS
    
1/ cập nhật hệ thống:

    sudo apt update && sudo apt upgrade -y
    
Cài đặt docker:

    sudo apt-get update
    sudo apt-get install \
    ca-certificates \
    curl \
    gnupg

Add key:

    sudo install -m 0755 -d /etc/apt/keyrings
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
    sudo chmod a+r /etc/apt/keyrings/docker.gpg

Cài source list:

    echo \
    "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
    "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
    sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

Cập nhật hệ thống:

    sudo apt-get update

Cài docker

    sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
    
2/ Thiết lập Dockerfile dự án:

    nano Dockerfile
    
Thay đổi các thông tin của bạn, dùng ví metamask:

    FROM elixirprotocol/validator:testnet-2

    ENV ADDRESS=
    ENV PRIVATE_KEY=
    ENV VALIDATOR_NAME=
    
Nhấn lưu lại bằng câu lệnh:

    Control + O
    Enter
    Control + X
    
Chạy lệnh cài đặt và chạy node:

    docker build . -f Dockerfile -t elixir-validator

    docker run -d --restart unless-stopped --name ev elixir-validator
    
Vào Dashboard dự án, dùng ví metamask mà bạn vừa điền ở Dockerfile kết nối, làm nhiệm vụ:

    https://dashboard.elixir.finance/
    
    - Faucet 1000 EXLR
    - Enroll tối thiểu 100 EXLR
    - Delegate vào địa chỉ ví: 0x19a03bdc95DCC47C3f9DebF7306D77fF24a9021F
   
Chúc các bạn thành công!
    


