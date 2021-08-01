<a href="https://github.com/NightwindDev/Preference-Bundle-Example/blob/main/README.md"><h1><- README.md</h1></a>

## PSButtonCell

This is a cell that - when pressed, does a certain action. This action can be specified in your `XXXRootListController.m` file.

Root.plist:

```xml
<dict>
	<key>action</key>
	<string>killPhoneApp</string>
	<key>cell</key>
	<string>PSButtonCell</string>
	<key>label</key>
	<string>Kill Phone App</string>
</dict>
```

XXXRootListController.m:

```objective-c
-(void)killPhoneApp {
	pid_t pid;
	const char* args[] = {"killall", "MobilePhone", NULL};
	posix_spawn(&pid, "/usr/bin/killall", NULL, NULL, (char* const*)args, NULL);
}
```

<img src="https://github.com/NightwindDev/Preference-Bundle-Example/blob/main/PSButtonCell.jpeg?raw=true" width="415">
