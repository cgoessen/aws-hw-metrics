# aws-hw-metrics
Simple Python script to collect and publish hardware metrcis

## Running in background

Using a cron rule:

```
*/5 * * * *   run_as   /usr/sbin/aws-hw-metrics -hddtd 7634 -ns Namespace -o /tmp/lastmetrics.json -last /tmp/lastmetrics.json -p
``` 

Adapt run_as and Namespace to your need.

## HDD temperatures

To track your hdd temperature, run hddtemp in daemon mode:

```
$ hddtemp /dev/sd* -d
```

And specify the port with -hddtd, 7634 by default.

## Publishing

Add `-p` or `--publish`.
Make sure the run_as user has aws credentials set up.
[https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html]

## Metric files

`-o` and `-last` are used to save and load metrics files respectively. The later is required to compute the disk and network delta usage
