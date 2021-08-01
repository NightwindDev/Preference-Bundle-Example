# Preference Bundle Example


## PSButtonCell

This is a cell that - when pressed, does a certain action. This action can be specified in your `XXXRootListController.m` file.

Example:

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

<div><img src="https://i.imgur.com/pDNGlKy.jpg" width="415">

## PSEditTextCell

This is a cell where text can be inputted and then later used in your tweak somewhere.

Root.plist:

```xml
<dict>
	<key>cell</key>
	<string>PSEditTextCell</string>
	<key>defaults</key>
	<string>com.nightwind.prefbundleexampleprefs</string>
	<key>label</key>
	<string>Text:</string>
	<key>key</key>
	<string>testedittextcellkey</string>
	<key>default</key>
	<string>default text</string>
	<key>id</key>
	<string>testedittextcellid</string>
</dict>
```

<div><img src="https://github.com/NightwindDev/Preference-Bundle-Example/blob/main/PSEditTextCell.jpeg?raw=true" width="415">

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
