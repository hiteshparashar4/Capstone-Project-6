# Capstone-Project-6
## Create a Linode server and install nginx server
- <img width="1112" height="279" alt="image" src="https://github.com/user-attachments/assets/dcad6f74-8f6c-4bf3-8eb3-e88ac76bee3c" />
- ssh to it
- <img width="965" height="365" alt="image" src="https://github.com/user-attachments/assets/b7ed1243-a64e-417f-b0ff-ae4a376a431d" />
- install docker
- <img width="1171" height="384" alt="image" src="https://github.com/user-attachments/assets/9af2fec8-72c1-44d7-b695-ed6d1bfe600a" />
- run nginx image
- <img width="1173" height="430" alt="image" src="https://github.com/user-attachments/assets/8ff6416c-decf-42bf-9e56-424c690ef972" />
- check if the app is accessible
- <img width="991" height="273" alt="image" src="https://github.com/user-attachments/assets/e8972087-5b55-47f4-b5d8-cafc36a7d256" />

## Write and execute python script to monitor the app and send a notification mail in case of an error
- write python script that monitors the website by pinging its dns address and checking status code - `monitor-webiste.py` - committed to this repo
- if status is 200, everything is fine, if not then send an email. The code to send the email is written in the script
- execute script `python ./monitor-website.py`
- <img width="414" height="215" alt="image" src="https://github.com/user-attachments/assets/2e2e50fb-ffc5-4c36-9e90-61fe394e604e" />

## Restart application
- the following function also restarts the application if app is accessible but not giving 200 status
```
  def restart_container():
    print('Restarting the application...')
    ssh = paramiko.SSHClient()
    ssh.set_missing_host_key_policy(paramiko.AutoAddPolicy())
    ssh.connect(hostname='172.104.252.104', username='root', key_filename='/Users/hitesh/.ssh/id_rsa')
    stdin, stdout, stderr = ssh.exec_command('docker start ee6b82b80ecd')
    print(stdout.readlines())
    ssh.close()
```
