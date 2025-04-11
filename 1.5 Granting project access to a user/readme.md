### Grant project access to a user

#### 1. Login with admin user, 
grant access to other user or group by running this command :
```bash
oc adm policy add-role-to-user <role> <username> -n <project/namespace>
oc adm policy add-role-to-group <role> <groupname> -n <project/namespace>
```

e.g :
```bash
oc adm policy add-role-to-user edit developer -n auto-rollout
```
