# Quartz(쿼츠) 활용 자바 스케줄링



Quartz(쿼츠)는 Java 언어를 통해 구축된 프로그램 작업을 스케줄링하기위해 사용하는 java Scheduling 라이브러리입니다. Java 소스코드 단계에서 작업 스케줄링이 가능하며, 다중 Thread Architecture 기반으로 동작합니다.



* 주요 Interface

  `Scheduler` - 스케줄링을 위한 기본 API

  `Job` - 실질적인 작업 수행 개체

​		`JobDetail` - Job 인스턴스 정의를 위해 사용

​		`Trigger` - Job(작업) 수행 일정을 위해 사용(시간, 횟수, 주기 등)

​		`JobBuilder` - JobDetail 생성을 위해 사용

​		`TriggerBuilder` - Trigger 생성을 위해 사용





* 작업주기 설정식

  `" 0 0 0 * * * "` : `" (seconds) (minutes) (hours) (day of month) (month) (day of week) (year) "`

  1. seconds - * / 0-59

  2. minutes - * / 0-59

  3. hours - * / 0-23

  4. day of month - * / 1-31 / ? / L / W / C

  5.  month - * / 1-12 / JAN-DEC
  6. day of week - * / 1-7 / SUN-SAT / ? / L / C / #
  7. year -  생략 / * / 1970-2099

ex) **작업주기 설정식 표**

| 식                             | 의미                                                         |
| ------------------------------ | ------------------------------------------------------------ |
| "0 0 12 * * *"                 | 매일 12:00 실행                                              |
| "0 15 10 ? * *"                | 매일 10:15 실행                                              |
| "0 15 10 * * ?"                | 매일 10:15 실행                                              |
| "0 15 10 * * ? **2005**"       | **2005년**의 매일 10:15 실행                                 |
| "0 * 14 * * ?"                 | 매일 14:00 ~ 14:59 매분마다 실행                             |
| "0 **0/5** 14**,**18 * * ?"    | 매일 14:00 ~ 14:59 **매5분 간격** 실행 **&**<br />매일 18:00 ~ 18:59 **매5분 간격** 실행 |
| "0 15 10 ? * **MON-FRI**"      | 매주 **월,화,수,목,금** 10:15 실행                           |
| "0 15 10 **L** * ?"            | 매월 **마지막날** 10:15 실행                                 |
| "0 15 10 ? * **6L** 2002-2005" | 2002~2005 매월 **마지막 금요일** 10:15 실행                  |
| "0 15 10 ? * **6#3**"          | 매월 **세번째 금요일** 10:15 실행                            |













크론탭을 이용해 리눅스 OS 단계에서 스케줄링이 가능하지만,

자바 소스 단게에서도 스케줄링이 가능합니다.



Quartz(쿼츠)를 활용해 자바 소스 단계에서 앱을 스케줄링하는 방법을 살펴보겠습니다.











ref)

https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=beanpole2020&logNo=221463397399

https://data-make.tistory.com/700

https://invincure.tistory.com/entry/Java-Quartz-%EC%BF%BC%EC%B8%A0%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%98%EC%97%AC-%EC%9E%90%EB%B0%94-%EC%8A%A4%EC%BC%80%EC%A4%84%EB%A7%81scheduling-%ED%95%98%EA%B8%B0









































