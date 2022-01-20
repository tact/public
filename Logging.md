# Tact logging

Tact produces a log as it operates. This log contains technical information about what exactly Tact does internally as you send and receive messages and do other actions on this device. Information from this log can be extremely useful to Tact team to diagnose and fix problems with Tact.

You can freely access the Tact log yourself on your devices, both to diagnose problems, and just inspecting yourself what Tact does if you’re curious.

For privacy reasons, Tact never sends its log anywhere automatically. The log always remains on the device where it is produced. If you wish to share the information from the log with anyone, you should extract the log yourself with the below instructions, verify what it contains, and only then share it.

## Simple log

You can access Tact’s recent log very simply in both macOS and iOS apps. Click or tap `Settings`, `Developer`. Scroll down and find `Application log`. Open it, and you see Tact’s recent log entries.

On iOS, use the Share button next to the log, to save or share the log into a good location, from where you could forward it to the Tact team. On macOS, there is a draggable widget there, which you can drag into your Desktop or Finder, to get the log as a text file.

## Advanced log

The simple log that you obtain above does not contain entries from earlier runs of Tact, and may also be otherwise incomplete. For more complex cases, you can obtain a more complete log with a bit more work. Its contents is the same as the simple log, it will just cover a longer time window.

You should run all the below commands in Terminal.

### macOS

When you start using Tact, turn on logging with this command:

```bash
sudo log config --mode "level:debug" --subsystem com.justtact.Tact
```

To see a live log as an app is running, run Terminal and enter the following command:

```bash
# Only Tact:
log stream --level debug --predicate 'subsystem == "com.justtact.Tact"' --style compact

# Tact and the Glitter XPC updater
log stream --level debug --predicate 'subsystem == "com.justtact.Tact.GlitterXPC" or subsystem == "com.justtact.Tact"' --style compact
```

If you then run Tact, you can see the logs live in Terminal window.

To get the log into text file, enter the following command:

```bash
log show --debug --info --predicate 'subsystem == "com.justtact.Tact"' > log.txt
```

The text file (can be any name) now contains your log.

### iOS

Working with Tact logs on iOS is a multi-step process. You must first collect logs from the device. Make sure there is only one device connected to your computer with a cable, and then run this command:

```bash
sudo log collect --device --last 28d
```

The last argument, 28d, shows the number of days to capture. It could also be less days if you are interested in a smaller period.

The system will ask you for your password, and then generate a `system_logs.logarchive` file into your current folder.

You can then analyze this log with a command like this:

```bash
log show --archive system_logs.logarchive --predicate 'subsystem =="com.justtact.Tact"' --debug --info --style compact
```

The above command prints all your Tact logs to terminal. If you instead would like to get these logs into a file, enter this command (log file name at the end can be anything):

```bash
log show --archive system_logs.logarchive --predicate 'subsystem =="com.justtact.Tact"' --debug --info --style compact > log.txt
```
