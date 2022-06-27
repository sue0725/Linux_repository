## 설치과정

_설치디스크 : CentOS-8-x86_64-1905-dvd.iso_

* 설치과정은 **이것이 리눅스다**를 참고하여 VMware를 보고 설치를 완료했으며 설정 명령어 정리 해보기!

---
### 자동 업데이트 기능을 끄기 위한 명령어
    gsetting set org.gnome.software download-updates false
    systemctl disable dnf-makecache.service
    systemctl disable dnf-makecache.timer


### dnf 명령
    dnf 명령은 CentOS의 소프트웨어를 설치할 때 사용하는 명령어


### 네트워크 장치 on, off
    nmcli connection down 장치이름 - 네트워크 장치 중지
    nmcli connection up 장치이름 - 네트워크 장치 시작
    reboot - 컴퓨터 재부팅

### 네트워크 정보 확인
    ifconfig 장치이름

### 해상도 조절
    gedit /etc/grub.d/10_linux
    한 뒤에 vga = *** 를 추가

### 패키지 설치
    dnf -y install firewall-config