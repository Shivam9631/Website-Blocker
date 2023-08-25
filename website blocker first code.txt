import time
from datetime import datetime as dt

redirect="127.0.0.1"
websites_list=["www.facebook.com","instagram.com","facebook.com","www.instagram.com"]
hosts_path="C:\Windows\System32\drivers\etc\hosts"

now=dt.now()
current_time=now.strftime("%H:%M:%S")
start_time="10:0:0"
end_time="17:0:0"
print(current_time)
while True:
    if start_time<=current_time and current_time<=end_time:
        print("working hours")
        with open(hosts_path,'r+') as file:
            content=file.read()
            for website in websites_list:
                if website in content:
                    pass
                
                else:
                    file.write(redirect+" "+website+"\n")
                    
    else:
        print("Non work hours")
        with open(hosts_path,'r+') as file:
            content=file.readlines()
            file.seek(0)
            for line in content:
                if not any(website in line for website in websites_list):
                    file.write(line)
            file.truncate()
            
    time.sleep(10)
    