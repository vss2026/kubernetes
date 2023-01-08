### Replication Controller, ReplicaSet - Template, Replicas, Selector

![Replication Controller, ReplicaSet - Template, Replicas, Selector](../images/Replication%20Controller%2C%20ReplicaSet%20-%20Template%2C%20Replicas%2C%20Selector1.png)

~~~
1. Auto Healing
- HTTP Health Check 사용 시 일정시간 응답이 없으면 인스턴스 재가동
- pod나 Node가 down 된 경우 다른 node에 pod를 다시 만들어줌

2. Auto Scaling
- 사용자가 정의한 주기(스케줄링)나 이벤트(모니터링 알람)에 따라 서버를 자동으로 생성하거나 삭제
- 서비스에 사용자가 늘어나는 경우에는 원활한 서비스를 위해 서버를 늘리고, 다시 여유로운 상황이 되면 불필요한 서버를 자동으로 줄여 발생하는 요금을 낮출 수 있다.

3. Software Update
- 여러 pod의 대해서 version 업을 해야하는 경우 controller를 이용해서 할 수 있으며
- rollback 기능도 사용 가능

4. Job
- 필요한 시점에 pod를 생성 후 삭제
- 효율적인 자원 관리가 가능
~~~


![Replication Controller, ReplicaSet - Template, Replicas, Selector](../images/Replication%20Controller%2C%20ReplicaSet%20-%20Template%2C%20Replicas%2C%20Selector2.png)


~~~
1. Template
- controller 와 pod 는 label과 selector로 연결 
- pod가 다운 되면 template의 있는 내용으로 pod를 새로 생성
- version upgrade 수동으로 가능 -> 새로운 version의 pod를 template에 등록 한뒤 기존의 pod를 다운 시킴

2. Replicas
- Replicas 수 만큼 pod의 개수가 관리
- pod가 제거시 Replicas 수 만큼 재생성

3. Selector
- ReplicaSet에만 있는 기능
- matchLabels - key value 모두 같아야 매칭
- matchExpressions - key value를 좀 더 detail 하게 설정 가능
  Exists = 해당 되는 key가 포함되어 있는가
  DoesNotExist = 해당 되는 key가 포함되어 있지 않은가
  In = key와 value를 지정 포함 되어있는지 확인
  NotIn = In과 반대 개념
~~~


# Reference
----
**ReplicaSet** : https://kubernetes.io/docs/concepts/workloads/controllers/replicaset/
**Labels and Selectors** : https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/
**ReplicationController** : https://kubernetes.io/docs/concepts/workloads/controllers/replicationcontroller/