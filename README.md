# Preference Bundle Example

<br/>

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

<img src="https://github.com/NightwindDev/Preference-Bundle-Example/blob/main/PSButtonCell.jpeg?raw=true" width="415">


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

<img src="https://github.com/NightwindDev/Preference-Bundle-Example/blob/main/PSEditTextCell.jpeg?raw=true" width="415">

## PSSecureEditTextCell

This is a cell where text can be inputted, secured in a password-style manner, and then later used in your tweak somewhere.

Root.plist:

```xml
<dict>
	<key>cell</key>
	<string>PSSecureEditTextCell</string>
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

<img src="https://github.com/NightwindDev/Preference-Bundle-Example/blob/main/PSSecureEditTextCell.jpeg?raw=true" width="415">

(The screenshot does not pick it up, but there are dots where the normal characters of the text field should be).

## PSEditTextViewCell

This cell is like PSEditTextCell, in the way that it is also an area for text input. Unlike PSEditTextCell, this cell expands the text input area to fit the whole cell.

This is a cell where text can be inputted, secured in a password-style manner, and then later used in your tweak somewhere.

Root.plist:

```xml
<dict>
	<key>cell</key>
	<string>PSEditTextViewCell</string>
	<key>defaults</key>
	<string>com.nightwind.prefbundleexampleprefs</string>
	<key>key</key>
	<string>testedittextcellkey</string>
	<key>default</key>
	<string>default text</string>
	<key>id</key>
	<string>testedittextcellid</string>
</dict>
```

<img src="https://github.com/NightwindDev/Preference-Bundle-Example/blob/main/PSEditTextViewCell.jpeg?raw=true" width="415">

## PSGiantCell

```xml
<dict>
	<key>cell</key>
	<string>PSGiantCell</string>
	<key>label</key>
	<string>Test</string>
</dict>
```

<img src="https://github.com/NightwindDev/Preference-Bundle-Example/blob/main/PSGiantCell.jpeg?raw=true" width="415">

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
