# crontab

list scheduled cron jobs

    crontab -l


open crontab editor (creates file if first time)

    crontab -e



# Basic Usage

entry format: mins hrs dayOfMonth month dayOfWeek /path/to/command

run a script every day at 2:30am

    30 2 * * * /path/to/script.sh


run every hour on the hour

    0 * * * * /path/to/script.sh


run every minute

    * * * * * /path/to/script.sh


