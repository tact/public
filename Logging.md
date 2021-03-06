# Tact logging

Tact produces logs as it operates. You can access this logs and attach them to bug reports as needed. You can also see them yourself and inspect what info they contain.

You should run all the below commands in Terminal.

## macOS

WHen you start using Tact, turn on logging with this command:

```bash
sudo log config --mode "level:debug" --subsystem eu.delta8.CChat
```

To see a live log as an app is running, run Terminal and enter the following command:

```bash
log stream --level debug --predicate 'subsystem == "eu.delta8.CChat"' --style compact
```

If you then run Tact, you can see the logs live in Terminal window.

To get the log into text file, enter the following command:

```bash
log show --debug --info --predicate 'subsystem == "eu.delta8.CChat"' > log.txt
```

The text file (can be any name) now contains your log.

## iOS

Working with Tact logs on iOS is a multi-step process. You must first collect logs from the device. Make sure there is only one device connected to your computer with a cable, and then run this command:

```bash
sudo log collect --device --last 28d
```

The last argument, 28d, shows the number of days to capture. It could also be less days if you are interested in a smaller period.

The system will ask you for your password, and then generate a `system_logs.logarchive` file into your current folder.

You can then analyze this log with a command like this:

```bash
log show --archive system_logs.logarchive --predicate 'subsystem =="eu.delta8.CChat"' --debug --info --style compact
```

The above command prints all your Tact logs to terminal. If you instead would like to get these logs into a file, enter this command (log file name at the end can be anything):

```bash
log show --archive system_logs.logarchive --predicate 'subsystem =="eu.delta8.CChat"' --debug --info --style compact > log.txt
```
