## Anisible Rolling udpates ## 

Deifintion - Why do I need a rolling udpate
Scenario: Lets say You are updating a cluster of webservers. The way ansible executes is that it **runs each task on all the managed hosts**, at the same time. Therefore it affects all the hosts which might cause a downtime. However we can avoid this issue if we update the servers in groups of 2 or 3 or whatever is convenient. This can be achieved using **Rolling Updates**

Rolling updates syntax
```
---
- name: rolling updates
  hosts: all
  serial: 2
  tasks:
    - name:
      yum: 
      .....
```

