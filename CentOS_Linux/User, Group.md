## 사용자와 그룹

리눅스는 다중 사용자 시스템이다. 즉 1대의 리눅스에 사용자 여러 명이 동시에 접속해서 사용할 수 있는 시스템이다.

기본적으로 root라는 이름을 가진 수퍼 유저가 있다. 이 root 사용자는 시스템의 모든 작업을 실행할 수 있는 권한이 있다.

---

* gedit나 vi 에디터로 /etc/passwd 파일을 열면 여러 명의 사용자가 보이는데 각 행의 의미는
    
        사용자 이름:암호:사용자ID:사용자가 소속된 그룹 ID:전체 이름:홈 디렉터리:기본 셸
_직접 /etc/passwd 파일을 열어서 확인해보는 게 좋음!_

## 사용자 및 그룹과 관련된 명령어

---
### **1. useradd**

_새로운 사용자를 추가해준다._

    * useradd newuser -> newuser라는 이름의 사용자 생성
    * useradd -u 1111 newuser -> newuser 사용자를 생성하면서 사용자 ID를 1111로 지정
    * useradd -g mygroup newuser -> newuser 사용자를 생성하면서 mygroup 그룹에 newuser 사용자를 포함시킴
    * useradd -d /newhome newuser -> newuser 사용자를 생성하면서 홈 디렉터리를 /newhome으로 지정
    * useradd -s /bin/csh newuser -> newuser 사용자를 생성하면서 기본 셸을 /bin/csh로 지정

### **2. passwd**

_사용자의 비밀번호를 지정하거나 변경한다._

    * passwd newuser -> newuser 사용자의 비밀번호 지정(또는 변경)

### **3. usermod**

_사용자의 속성을 변경한다._

    * usermod -g root newuser -> newuser 사용자의 그룹을 root 그룹으로 변경

### **4. userdel**

_사용자를 삭제한다._

    * userdel newuser- > newuser 사용자 삭제
    * userdel -r newuser -> newuser 사용자를 삭제하면서 홈 디렉터리까지 삭제

### **5. chage**

_사용자의 암호를 주기적으로 변경하도록 설정한다._

    * chage -1 newuser ->newuser 사용자에 설정된 사항 확인
    * chage -m 2 newuwer -> newuser 사용자에 설정한 암호를 사용해야 하는 최소 일자
    * chage -M 30 newuser -> newuser 사용자에 설정한 암호를 사용할 수 있는 최대 일자
    * chage -E 2026/12/12 newuser -> newuser 사용자에 설정한 암호가 만료되는 날짜
    * chage -10 newuser -> newuser 사용자에 설정한 암호가 만료되기 전에 경고하는 기간 지정하지 않을 경우 기본값은 7일

### **6. groups**

_사용자가 소속된 그룹을 보여준다._

    * groups -> 현재 사용자가 소속된 그룹을 보여줌
    * groups newuwer -> newuser가 소속된 그룹을 보여줌

### **7. groupadd**

_새로운 그룹을 생성한다._

    * groupadd newgroup -> newgroup 이라는 그룹 생성
    * groupadd -g 2222 newgroup -> newgroup 이라는 그룹을 생성하면서 그룹 ID를 2222로 지정

### **8. groupmod**

_그룹의 속성을 변경한다._

    * groupmod -n mygroup newgroup -> newgroup 그룹의 이름을 mygroup으로 변경

### **9. groupdel**

_그룹을 삭제한다._

    * groupdel newgroup -> newgroup 그룹 삭제

### **10. gpasswd**

_그룹의 암호를 설정하거나 그룹 관리를 수행한다._

    * gpasswd newgroup -> newgroup 그룹의 암호 지정
    * gpasswd A newuser newgroup -> newuser 사용자를 newgroup 그룹의 관리자로 지정
    * gpasswd -a user1 new group -> user1을 newgroup의 사용자로 추가
    * gpasswd -d user1 new group -> user1을 newgroup 그룹의 사용자에서 제거