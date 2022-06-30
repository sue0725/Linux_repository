## cron

* 주기적으로 반복되는 일을 자동으로 실행할 수 있도록 시스템 작업을 예약해 놓는 것을 cron 이라 부른다.

* cron과 관련된 데몬(서비스)은 crond이고, 관련 파일은 /etc/crontab 이다.

* /etc/crontab의 형식
    
    **분 시 일 월 요일 사용자 실행명령**

    **00 05 01 12 root cp -r /home /backup**

### crontab 파일과 관련 디렉터리

    * /etc/cron.hourly/ : 시간별
    * /etc/cron.daily/ : 일별
    * /etc/cron.weekly/ : 주별
    * /etc/cron.monthly/ : 월별
    
## at

* cron은 주기적으로 반복되는 작업을 예약하는 것이지만, at 명령어는 일회성 작업을 예약하는 것이다. 즉, 예약해두면 한 번만 실행되고 소멸된다.

    * 예약 : at 시간
    * 확인 : at -l
    * 취소 : atrm 작업번호


