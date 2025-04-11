### Creating a User
------
#### 1. Start crc by running this following command.
```bash
crc start
```
wait until the cluster is running.
<img src="" alt="start cluster running"/>
#### 2. Download apache2-utils.
```bash
sudo apt install apache2-utils
```
#### 3. Add new user to existing secret.
login to ocp using admin :
```bash
oc login <openshift URL> -u <openshift admin username> -p <openshift admin password>
```
or copy login command from login ui :
<img src="" alt="login1"/>
<img src="" alt="login2"/>
<img src="" alt="login3"/>

first we need to get existing secret by running this command :
```bash
oc get secret htpass-secret -n openshift-config -o jsonpath='{.data.htpasswd}' | base64 -d > users.htpasswd
```
<img src="" alt="get secret user"/>

and then modify add new user by running this command :
```bash
htpasswd -B -b users.htpasswd developer-dummy password123
```
<img src="" alt="add new user"/>

check the data in users.htpasswd :
```bash
nano users.htpasswd
```
<img src="" alt="data user"/>

#### 4. Apply the updated secret
```bash
oc create secret generic htpass-secret --from-file=htpasswd=users.htpasswd -n openshift-config --dry-run=client -o yaml | oc apply -f -
```

#### 5. Verify process by checking user management in openshift console.
<img src="" alt="user-management"/>
