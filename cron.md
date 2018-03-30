
**Step 1:** Open a Terminal Window (Command Line) in Linux. 

**Step 2:** The following is a list of cron directories:
* /etc/cron.hourly
* /etc/cron.daily
* /etc/cron.weekly
* /etc/cron.monthly

Copy your shell script `script.sh` or `script` into one of the directories above.
If you need to run the script hourly, place your script file in the “cron.hourly”
folder. For daily, place it inside the “cron.daily” and so forth. 

**Step 3:** Give the shell script the correct permission. For example, if script is called
“script.sh”, set permission as follows: 

`cd /etc/cron.daily/`   
`chmod 755 script.sh` 

**Step 4:** Add new cron job to crontab: 

```crontab –e```

This opens vi editor for you. Create the cron command using the following syntax:
1. The number of minutes after the hour (0 to 59)
2. The hour in military time (24 hour) format (0 to 23)
3. The day of the month (1 to 31)
4. The month (1 to 12)
5. The day of the week(0 or 7 is Sun, or use name)
6. The command to run

# 
**More graphically they would look like this:**
```
 * * * * *  command to execute
 ┬ ┬ ┬ ┬ ┬
 │ │ │ │ │
 │ │ │ │ │
 │ │ │ │ └───── day of week (0 - 7) (0 to 6 are Sunday to Saturday, or use names; 7 is Sunday, the same as 0)
 │ │ │ └────────── month (1 - 12)
 │ │ └─────────────── day of month (1 - 31)
 │ └──────────────────── hour (0 - 23)
 └───────────────────────── min (0 - 59)
```


**Example 1**: command would be **0 0 * * * /etc/cron.daily/script.sh**. This
would mean that the shell script will exactly execute at midnight every
night.

**Example 2**: add a new line in `crontab -e` which runs a laravel artisan command every 1 minute `*/1 * * * * php ~/Documents/localdev/bonjour/artisan email:notransaction`

`0-55/5 * * * *` is the same as `*/5` means your command will run at every 5 minutes  
`* * * * *` Every minute of every day of every week of every month, that command runs.
**For more**
`man crontab` for cron manual



To save the changes to the crontab that you just made, hit ESC key, and
then type :w followed by :q to exit.
**To list existing cron jobs:**
 ```crontab –l```
To remove an existing cron job:
• Enter: crontab –e
• Delete the line that contains your cron job
• Hit ESC > :w > :q

