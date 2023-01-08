### DaemonSet, Job, CronJob

![DaemonSet, Job, CronJob](../images/DaemonSet%2C%20Job%2C%20CronJob1.png)

```

```

![DaemonSet, Job, CronJob](../images/DaemonSet%2C%20Job%2C%20CronJob2.png)

```
1. DaemonSet
- ReplicaSet이랑 다르게 DaemonSet은 자원 상태에 따른 pod 배치가 아닌 동일 배치
- 이와 같은 특성은 각 pod가 존재해야하는 서비스가 존재 하기 떄문 (prometheus, fluentd, GlusterFs)

2. Job
- node 장애 발생시 pod는 down, 
- replicaSet으로 만들어진 pod는 다른 node에 recreate 후 restart
- job으로 만들어진 pod는 다른 node에 recreate 후 finish 
- options
  completions - 몇개의 pod를 만들것인가
  parallelism - pod를 몇개씩 생성할 것 인가
  activeDeadlineSeconds - job이 일정 시간이 지나면 자동 삭제 실행중이거나 실행이 안된 pod도 모두 삭제

3. Cronjob
- 특정 시간에 job을 실행하기 위함
- Cronjob 삭제시 Manual로 만든 Job도 같이 삭제됨
- db백업, 업데이트 확인, message발송 ...
- concurencyPolicy
  Allow - default, 시간설정 단위로 job이 만들어짐
  Forbid - pod가 존재 하면 skip
  Replace - pod가 running중이면 기존pod는 삭제 후 새 pod를 생성
```


# Reference
----
**Jobs** : https://kubernetes.io/docs/concepts/workloads/controllers/job/
**CronJob** : https://kubernetes.io/docs/concepts/workloads/controllers/cron-jobs/
**Running Automated Tasks with a CronJob** : https://kubernetes.io/docs/tasks/job/automated-tasks-with-cron-jobs/