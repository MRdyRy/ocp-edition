### Adding policies to a user

#### 1. Cluster
add admin role to user :
```bash
oc adm policy add-cluster-role-to-user cluster-admin rudyryanto
```

#### 2. Role
add role to user :
```bash
oc adm policy add-role-to-user [role] [username] -n [namespace]
```
role :
- create
- view
- edit
- delete

example :
```bash
oc adm policy add-role-to-user view developer -n auto-rollout
```
