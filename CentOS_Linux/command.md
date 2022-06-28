## 리눅스 기본 명령어 정리

### 터미널/콘솔에서 시스템 종료 명령 실행
    poweroff, shutdown -P now, halt -p, init0

### shutdown 명령어 옵션
    shutdown -P +10     -> 10분 후 종료(P:poweroff)
    shutdown -r 22:00   -> 오후 10시에 재부팅(r:reboot)
    shutdown -c         -> 예약된 shutdown 취소(c:cancle)
    shutdown -k + 15    -> 현재 접속한 사용자에게 15분 후 종료된다는 메세지를 보내지만 실제로는 종료되지 않음

### 재부팅 명령어
    shutdown -r now, reboot, init6

### 로그아웃
    (텍스트 모드) logout, exit

### 가상 콘솔
    ctrl + alt + F1 ~ F6 까지

---

## 런레벨

_init 명령 뒤에 붙는 숫자를 런레벨이라고 부른다._

### 런레벨 확인
    ls -l /etc/systemd/system/default.target

### 텍스트 모드로 부팅되도록 런레벨 변경
    ln -sf /lib/systemd/system/multi-user.target /etc/systemd/systemdefault.target

### 도스 키
    history     -> 기존에 사용했던 명령을 모두 보기
    history -c  -> 저장되었던 명령을 모두 삭제

### 파일 내용 확인
    cat ifcfg-ens160(파일이름)

### 에디터
    vi, gedit

### 스왑 파일 삭제
    ls -a
    rm -f .test1.txt.swp

### 도움말 사용법
    man <명령어>