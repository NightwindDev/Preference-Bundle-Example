# Preference Bundle Example

## Universal Keys

**PostNotification** - adds a way for the tweak to communicate with the preference bundle
```xml
<key>PostNotification</key>
<string>com.nightwind.prefbundleexampleprefs-updated</string>
```

**height** - determines the height of the cell 
```xml
<key>height</key>
<string>66</string>
```

**id** - gives a unique identifier to the cell
```xml
<key>id</key>
<string>testCellId</string>
```

**key** - unique identifier to the cell, which can later be used when <a href ="https://github.com/NightwindDev/Preference-Bundle-Example/blob/main/README.md#linking-cells-to-tweak">linking the cells to the main tweak file.</a>
```xml
<key>key</key>
<string>testCellKey</string>
```

<br/>

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
	<key>defaults</key>
	<string>com.nightwind.prefbundleexampleprefs</string>
</dict>
```

XXXRootListController.m:

```logos
-(void)killPhoneApp {
	pid_t pid;
	const char* args[] = {"killall", "MobilePhone", NULL};
	posix_spawn(&pid, "/usr/bin/killall", NULL, NULL, (char* const*)args, NULL);
}
```

<img src="https://github.com/NightwindDev/Preference-Bundle-Example/blob/main/PSButtonCell.jpeg" width="415">


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
	<key>default</key>
	<string>default text</string>
</dict>
```

<img src="https://github.com/NightwindDev/Preference-Bundle-Example/blob/main/PSSecureEditTextCell.jpeg?raw=true" width="415">

(The screenshot does not pick it up, but there are dots where the normal text characters of the text field should be).

## PSEditTextViewCell

This cell is like PSEditTextCell, in the way that it is also an area for text input. Unlike PSEditTextCell, this cell expands the text input area to fit the whole cell.

Root.plist:

```xml
<dict>
	<key>cell</key>
	<string>PSEditTextViewCell</string>
	<key>defaults</key>
	<string>com.nightwind.prefbundleexampleprefs</string>
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

```logos
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

```logos
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


Root.plist:

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

## PSSegmentCell

This is a segmented cell, which can have multiple values inputted into it.


Root.plist:

```xml
<dict>
	<key>cell</key>
	<string>PSSegmentCell</string>
	<key>default</key>
	<integer>0</integer>
	<key>label</key>
	<string>Test</string>
	<key>validTitles</key>
	<array>
		<string>test 1</string>
		<string>test 2</string>
		<string>test 3</string>
	</array>
	<key>validValues</key>
	<array>
		<integer>0</integer>
		<integer>1</integer>
		<integer>2</integer>
	</array>
</dict>
```

<img src="https://github.com/NightwindDev/Preference-Bundle-Example/blob/main/PSSegmentCell.jpeg?raw=true" width="415">

## PSSliderCell

This is a cell which contains a slider. The slider can be dragged and have multiple output values based on where the knob is located.

Root.plist:

```xml
<dict>
	<key>cell</key>
	<string>PSSliderCell</string>
	<key>default</key>
	<real>66</real>
	<key>min</key>
	<integer>0</integer>
	<key>max</key>
	<integer>50</integer>
</dict>
```

<img src="https://github.com/NightwindDev/Preference-Bundle-Example/blob/main/PSSliderCell.jpeg?raw=true" width="415">

## PSSpinnerCell

This cell is a cell which has a spinner inside of it. This cell is meant to be inserted before an actual cell is loaded and then deleted.


Root.plist:

```xml
<dict>
	<key>cell</key>
	<string>PSSpinnerCell</string>
	<key>label</key>
	<string>Test</string>
</dict>
```

<img src="https://github.com/NightwindDev/Preference-Bundle-Example/blob/main/PSSpinnerCell.jpeg?raw=true" width="415">

## PSStaticTextCell

This is a cell which just has text.


Root.plist:

```xml
<dict>
	<key>cell</key>
	<string>PSStaticTextCell</string>
	<key>label</key>
	<string>Test</string>
</dict>
```

<img src="https://github.com/NightwindDev/Preference-Bundle-Example/blob/main/PSStaticTextCell.jpeg?raw=true" width="415">

## PSSwitchCell

This is a cell which has a switch in it, and the value of the switch can be used in the tweak.


Root.plist:

```xml
<dict>
	<key>cell</key>
	<string>PSSwitchCell</string>
	<key>default</key>
	<true/>
	<key>label</key>
	<string>Test</string>
</dict>
```

<img src="https://github.com/NightwindDev/Preference-Bundle-Example/blob/main/PSSwitchCell.jpeg?raw=true" width="415">

<br/>

# Linking Cells to Tweak

The code below shoould be put above `%hook`s and, if present, `%group`s as well. 

```logos
static BOOL testSwitchKey; // PSSwitchCell
static NSInteger testSegmentkey; // PSSegmentCell
static NSInteger testSliderKey; // PSSliderCell
static NSString *testEditTextKey; // PSEditTextCell or PSSecureEditTextCell
```

The code below should be put in the main `Tweak.x`/`Tweak.xm` file.

```logos
void preferencesChanged(){
	NSDictionary *prefs = [[NSUserDefaults standardUserDefaults] persistentDomainForName:@"com.nightwind.prefbundleexampleprefs"];

	testSwitchKey = (prefs && [prefs objectForKey:@"testSwitchKey"] ? [[prefs valueForKey:@"testSwitchKey"] boolValue] : YES ); // PSSwitchCell
	testSegmentKey = (prefs && [prefs objectForKey:@"testSegmentKey"] ? [[prefs valueForKey:@"testSegmentKey"] integerValue] : 0 ); // PSSegmentCell
	testSliderKey = (prefs && [prefs objectForKey:@"testSliderKey"] ? [[prefs valueForKey:@"testSliderKey"] floatValue] : 30 ); // PSSliderCell
	testEditTextKey = [prefs objectForKey:@"testEditTextKey"]; // PSEditTextCell or PSSecureEditTextCell
}

%ctor{
	preferencesChanged();

	CFNotificationCenterAddObserver(CFNotificationCenterGetDarwinNotifyCenter(), NULL, (CFNotificationCallback)preferencesChanged, CFSTR("com.nightwind.prefbundleexampleprefs-updated"), NULL, CFNotificationSuspensionBehaviorDeliverImmediately);
}
```

The key in the `Tweak.x`/`Tweak.xm` file should of course correspond to the key in the .plist file.

So for example say there's a enable tweak switch in the preference bundle, which looks like this:

```xml
<dict>
	<key>cell</key>
	<string>PSSwitchCell</string>
	<key>default</key>
	<true/>
	<key>label</key>
	<string>Enable tweak</string>
	<key>key</key>
	<string>tweakEnabled</string>
	<key>PostNotification</key>
	<string>com.nightwind.prefbundleexampleprefs-updated</string>
</dict>
```

In the `Tweak.x`/`Tweak.xm` file, there should be this at the top:

```logos
static BOOL tweakEnabled;
```

...and this at the bottom:

```logos
tweakEnabled = (prefs && [prefs objectForKey:@"tweakEnabled"] ? [[prefs valueForKey:@"tweakEnabled"] boolValue] : YES );
```

**Note:** If the default in the switch in the preference bundle is true, then the default should be `YES` in the `Tweak.x`/`Tweak.xm` file as well. If the default is set to false, then the default in the `Tweak.x`/`Tweak.xm` file should be `NO`.

Root.plist:

```xml
<key>default</key>
<true/>
```

Tweak.x:

```logos
tweakEnabled = (prefs && [prefs objectForKey:@"tweakEnabled"] ? [[prefs valueForKey:@"tweakEnabled"] boolValue] : YES );
```
*It says `YES` at the very end so that corresponds to the .plist file.*

# Further Information

https://iphonedev.wiki/index.php/Preferences_specifier_plist
