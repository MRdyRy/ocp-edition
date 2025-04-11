### Creating a User
------
#### 1. Start crc by running this following command.
```bash
crc start
```
wait until the cluster is running.
<img src="https://github.com/MRdyRy/ocp-edition/blob/main/1.2%20Creating%20a%20user/assets/crc%20start%20log.png" alt="start cluster running"/>
<img src="https://github.com/MRdyRy/ocp-edition/blob/main/1.2%20Creating%20a%20user/assets/login1.png" alt="start cluster running"/>
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
<img src="https://github.com/MRdyRy/ocp-edition/blob/main/1.2%20Creating%20a%20user/assets/login0.png" alt="login0"/>
<img src="https://github.com/MRdyRy/ocp-edition/blob/main/1.2%20Creating%20a%20user/assets/login1.png" alt="login1"/>
<img src="https://github.com/MRdyRy/ocp-edition/blob/main/1.2%20Creating%20a%20user/assets/login2.png" alt="login2"/>
<img src="https://github.com/MRdyRy/ocp-edition/blob/main/1.2%20Creating%20a%20user/assets/login3.png" alt="login3"/>

first we need to get existing secret by running this command :
```bash
oc get secret htpass-secret -n openshift-config -o jsonpath='{.data.htpasswd}' | base64 -d > users.htpasswd
```

and then modify add new user by running this command :
```bash
htpasswd -B -b users.htpasswd developer-dummy password123
```
<img src="https://github.com/MRdyRy/ocp-edition/blob/main/1.2%20Creating%20a%20user/assets/Screenshot%20from%202025-04-11%2018-19-29.png" alt="add new user"/>

check the data in users.htpasswd :
```bash
nano users.htpasswd
```
<img src="https://github.com/MRdyRy/ocp-edition/blob/main/1.2%20Creating%20a%20user/assets/Screenshot%20from%202025-04-11%2018-19-43.png" alt="data user"/>

#### 4. Apply the updated secret
```bash
oc create secret generic htpass-secret --from-file=htpasswd=users.htpasswd -n openshift-config --dry-run=client -o yaml | oc apply -f -
```
<img src="https://github.com/MRdyRy/ocp-edition/blob/main/1.2%20Creating%20a%20user/assets/Screenshot%20from%202025-04-11%2018-23-47.png" alt="apply"/>

#### 5. Verify process by checking user management in openshift console.
<img src="https://github.com/MRdyRy/ocp-edition/blob/main/1.2%20Creating%20a%20user/assets/user-management.png" alt="user-management"/>
