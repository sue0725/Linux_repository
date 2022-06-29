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

---

## 마운트(moount)

_물리적인 장치를 특정한 위치(대개는 폴더)에 연결시키는 과정_

    mount -> 현재 마운트 된 장치들을 확인

    umount /dev/cdrom -> 마운트 해제

### 현재 디렉터리 위치
    pwd (print working directory)

_텍스트 모드에서는 CD/DVD를 넣거나 USB 메모리를 연결했다고 자동으로 마운트 되는 것이 아니다!_

* CD/DVD 장치 이름은 전통적인 /dev/cdrom으로 제공된다 
        
        ls /dev/sd* 명령을 사용하여 장치 이름 확인

---

# 리눅스 기본 명령어

## ls

_LiSt의 약자로 Windows의 'dir'과 같은 역할을 한다. 즉 해당 디렉터리(=폴더)에 있는 파일의 목록 나열_

    * ls                        -> 현재 디렉터리의 파일 목록
    * ls /etc/sysconfig         -> /etc/sysconfig 디렉터리의 목록
    * ls -a                     -> 현재 디렉터리의 목록
    * ls -l                     -> 현재 디렉터리의 목록을 자세히 보여줌
    * ls *.cfg                  -> 확장자가 cfg인 목록을 보여줌
    * ls -l /etc/sysconfig/a*   -> /etc/sysconfig 디렉터리에 있는 목록 중 앞 글자가 'a'인 것의 목록을 자세히 보여줌

## cd

_Change Directory의 약자로 디렉터리를 이동하는 명령이다._

    * cd                    -> 현재 사용자의 홈 디렉터리로 이동
    * cd ~centos            -> centos 사용자의 홈 디렉터리로 이동
    * cd ..                 -> 바로 상위의 디렉터리로 이동
    * cd /etc/sysconfig     -> /etc/sysconfig 디렉터리로 이동(절대경로)
    * cd ../etc/sysconfig   -> 상대 경로로 이동


## rm

_ReMove의 약자로, 파일이나 디렉터리를 삭제한다._

    * rm abc.txt -> 해당 파일 삭제(내부적으로 'rm -i'로 연결됨)
    * rm -i abc.txt -> 삭제 시 정말 삭제할 지 확인하는 메세지가 나옴
    * rm -f abc.txt -> 삭제 시 확인하지 않고 바로 삭제함(f는 Force의 약자)
    * rm -r abc -> 해당 디렉터리 삭제(r은 Recursive의 약자)
    * rm -rf abc -> r옵션과 f옵션을 합친 것으로, abc 디렉터리와 그 아래에 있는 하위 디렉터리를 강제로 전부 삭제

## copy

_CoPy의 약자로, 파일이나 디렉터리를 복사한다._

    * cp abc.txt cba.txt -> abc.txt를 cba.txt라는 이름으로 바꿔서 복사
    * cp -r abc cba      -> 디렉터리 복사

## touch

_크기가 0인 새 파일을 생성하거나, 이미 파일이 존재한다면 파일의 최종 수정 시간을 변경한다._

    * touch abc.txt -> 파일이 없을 경우 abc.txt 라는 빈 파일을 생성하고, 이미 있을 경우 파일의 최종 수정 시간을 현재 시각으로 변경

## mv

_MoVe의 약자로, 파일이나 디렉터리의 이름을 변경하거나 다른 디렉터리로 옮길 때 사용한다._

    * mv abc.txt /etc/sysconfig -> abc.txt를 /etx/sysconfig/ 디렉터릴 이동
    * mv aaa bbb ccc ddd        -> aaa, bbb, ccc 파일을 /ddd 디렉터리로 이동
    * mv abc.txt www.txt        -> abc.txt의 이름을 www.txt로 변경해서 이동

## mkdir

_MaKe DIRectory의 약자로, 새로운 디렉터리 생성한다._

    * mkdir abc         -> 현재 디렉터리 아래에 /abc 이름의 디렉터리 생성
    * mkdir -p /def/fgh -> /def/fgh 디렉터리를 생성하는데, 만약 /fgh 디렉터리의 부모 디렉터리인 '/def' 디렉터리가 없다면 자동 생성해줌(p는 Parents)

## rmdir

_ReMoveDIRectory의 약자로, 디렉터리를 삭제한다._

    * rmdir abc -> /abc 디렉터리 삭제

## cat

_conCATenate의 약자로, 파일 내용을 화면에 보여준다._

    * cat a.txt -> a.txt 파일의 내용을 화면에 보여줌

## head, tail

_텍스트 형식으로 작성된 파일의 앞 10행 또는 마지막 10행만 화면에 출력한다._

    * head anaconda-ks.cfg    -> 해당 파일의 앞 10행을 화면에 출력
    * head -3 anaconda-ks.cfg -> 앞 3행만 화면에 출력
    * tail -5 anaconda-ks.cfg -> 마지막 5행만 화면에 출력

## more

_텍스트 형식으로 작성된 파일을 페이지 단위로 화면에 출력한다._

    * more anaconda-ks.cfg 
    * more +100 anaconda-ks.cfg -> 100행부터 출력

## less

_more 명령과 용도가 비슷하지만 기능이 더 확장되어 있다._

    * less anaconda-ks.cfg
    * less +100 anaconda-ks.cfg -> 100행 부터 출력

## file

_해당 파일이 어떤 종류의 파일인지 표시해준다._
    
    * file anaconda-ks.cfg -> 텍스트 파일이므로 아스키 파일로 표시됨
    * file /dev/sr0        -> sr0은 DVD 장치이므로 block special로 표시됨

