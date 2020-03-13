# Automation
Automation tools such as `cronjob` or `at`


# Resources
- [Cronjob scheduler](https://crontab.guru/)
- [`at` intro](https://www.computerhope.com/unix/uat.htm)

# Cronjob
Usage: When you need to schedule a multiple-run job

Open cronjob editor
```
crontab -e
```

List cronjobs
```
crontab -l
```

Sample cronjob: Runs python script on Sunday, March 1st at 11:00am
```bash
0 11 1 3 * python3 /root/atmo-workshop-scripts/batch_update_allocation.py --csv="/root/atmo-workshop-scripts/file.csv" --token="MY_API_KEY" >> ~/output.txt
```


# At
Usage: When you need to schedule a single-run job

List at jobs
```
atq
```

Create at job: Run script 1 minute from now
```
at now + 1 minute
at> bash some_script.sh
at> CTRL+d
```

Create at job: Run script on some date
```
at 7:00 AM 04/01
at> bash some_script.sh
at> echo "hello world" > ~/out.txt
```