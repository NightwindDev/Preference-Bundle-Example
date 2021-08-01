# Preference Bundle Example


## PSButtonCell

This is a cell that - when pressed, does a certain action. This action can be specified in your `XXXRootListController.m` file.

Example:

`root.plist`

```
<dict>
			<key>action</key>
			<string>killPhoneApp</string>
			<key>cell</key>
			<string>PSButtonCell</string>
			<key>label</key>
			<string>Kill Phone App</string>
</dict>
```

`XXXRootListController.m`

```
-(void)killPhoneApp {
	pid_t pid;
	const char* args[] = {"killall", "MobilePhone", NULL};
	posix_spawn(&pid, "/usr/bin/killall", NULL, NULL, (char* const*)args, NULL);
}
```

## PSEditTextCell

test test test

## PSEditTextViewCell

test test test

## PSGiantCell

test test test

## PSGiantIconCell

test test test

## PSGroupCell

test test test

## PSLinkCell

test test test

## PSLinkListCell

test test test

## PSListItemCell

test test test

## PSSecureEditTextCell

test test test

## PSSegmentCell

test test test

## PSSliderCell

test test test

## PSSpinnerCell

test test test

## PSStaticTextCell

test test test

## PSSwitchCell

test test test

## PSTitleValueCell

test test test
