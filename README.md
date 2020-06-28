## Anisible Rolling udpates using include_tasks
This repo is a playbook for installing webserver using rolling updates and include_tasks.

1. Rolling updates
Deifintion - Why do I need a rolling udpate
Scenario: Lets say You are updating a cluster of webservers. The way ansible executes is that it **runs each task on all the managed hosts**, at the same time. Therefore it affects all the hosts which might cause a downtime. However we can avoid this issue if we update the servers in groups of 2 or 3 or whatever is convenient. This can be achieved using **Rolling Updates**

```
---
- name: rolling updates
  hosts: all
  **serial: 2**
  tasks:
    - name:
      yum: 
      .....
```
2. Include_tasks
Include tasks is a way to distribute each task in seperate playbook files. One important aspect of **include_tasks** is that it is very memory friendly. The main playbook calls the children playbooks **one by one** therefore all playbooks are not loaded at the same time. It **dynamically** allocates the memory on the control nodes as and when they are called (as opposed to *import_tasks*)


