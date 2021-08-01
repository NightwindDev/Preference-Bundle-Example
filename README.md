# Preference Bundle Example

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
</dict>
```

<img src="https://github.com/NightwindDev/Preference-Bundle-Example/blob/main/PSSecureEditTextCell.jpeg?raw=true" width="415">

(The screenshot does not pick it up, but there are dots where the normal characters of the text field should be).

## PSEditTextViewCell

This cell is like PSEditTextCell, in the way that it is also an area for text input. Unlike PSEditTextCell, this cell expands the text input area to fit the whole cell.

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
</dict>
```

<img src="https://github.com/NightwindDev/Preference-Bundle-Example/blob/main/PSEditTextViewCell.jpeg?raw=true" width="415">

## PSGiantCell

This is a cell that is larger than normal cells. This cell can take an action assigned to it, just like PSButtonCell.


Root.plist:

```xml
<dict>
	<key>cell</key>
	<string>PSGiantCell</string>
	<key>label</key>
	<string>Test</string>
	<key>action</key>
	<string>respring</string>
</dict>
```

XXXRootListController.m:

```objective-c
-(void)respring {
	pid_t pid;
	const char* args[] = {"killall", "SpringBoard", NULL};
	posix_spawn(&pid, "/usr/bin/killall", NULL, NULL, (char* const*)args, NULL);
}
```

<img src="https://github.com/NightwindDev/Preference-Bundle-Example/blob/main/PSGiantCell.jpeg?raw=true" width="415">

## PSGiantIconCell

This cell is similar to PSGiantCell in the terms of size, however it has an option to put an icon into it.
Your icon should be placed in your `Resources` folder and should be named accordingly to your plist. This cell also allows for an action, just like the PSGiantCell mentioned above.

Root.plist:

```xml
<dict>
	<key>cell</key>
	<string>PSGiantIconCell</string>
	<key>label</key>
	<string>Test</string>
	<key>icon</key>
	<string>testicon.png</string>
	<key>action</key>
	<string>killSettingsApp</string>
</dict>
```

XXXRootListController.m:

```objective-c
-(void)killSettingsApp {
	pid_t pid;
	const char* args[] = {"killall", "Preferences", NULL};
	posix_spawn(&pid, "/usr/bin/killall", NULL, NULL, (char* const*)args, NULL);
}
```

In this case, the icon is named `testicon.png`, so the image in your `Resources` folder should be named `testicon.png` as well. If you want to look at the icon in Filza on device, you can find it in `/Library/PreferenceBundles/YourBundleName.bundle/`.


<img src="https://github.com/NightwindDev/Preference-Bundle-Example/blob/main/PSGiantIconCell.jpeg?raw=true" width="415">

## PSGroupCell

PSGroupCell is a really useful cell that allows for seperation of large clusters of cells. 

Root.plist:

```xml
<dict>
	<key>cell</key>
	<string>PSGroupCell</string>
	<key>label</key>
	<string>PSGroupCell Test</string>
</dict>

```

<img src="https://github.com/NightwindDev/Preference-Bundle-Example/blob/main/PSGroupCell.jpeg?raw=true" width="415">

(Pictured here: 2 PSGiantIconCells, which are the ones with the icons, and PSGroupCells above them).

## PSLinkCell

This cell is used to link to a different view controller. For example in this code snippet, the cell leads to `PSUIPrefsListController` which is the main Settings app page.

Root.plist:

```xml
<dict>
	<key>cell</key>
	<string>PSLinkCell</string>
	<key>detail</key>
	<string>PSUIPrefsListController</string>
	<key>icon</key>
	<string>icon.png</string>
	<key>isController</key>
	<true/>
	<key>label</key>
	<string>test label</string>
</dict>
```

<img src="https://github.com/NightwindDev/Preference-Bundle-Example/blob/main/PSLinkCell.jpeg?raw=true" width="415">

## PSLinkListCell

This cell is used to link to a predefined view controller, which has the cells inside of it defined here.

```xml
<dict>
	<key>cell</key>
	<string>PSLinkListCell</string>
	<key>detail</key>
	<string>PSListItemsController</string>
	<key>label</key>
	<string>Test 1</string>
	<key>validTitles</key>
	<array>
		<string>List Test 1</string>
		<string>List Test 2</string>
	</array>
	<key>validValues</key>
	<array>
		<integer>0</integer>
		<integer>1</integer>
	</array>
</dict>
```

<img src="https://github.com/NightwindDev/Preference-Bundle-Example/blob/main/PSLinkListCell.gif?raw=true" width="415">

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
