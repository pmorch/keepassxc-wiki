When using autotype you can select witch Window you want inject key to when Autotype is performed.

Once you perform Autotype (by pressing the shortcut key) KeePassXC will check for match between the focused Window Title and every Entry Autotype-WindowTitle settings.
If at least a match is found, a prompt will ask you to select the Entry you want to inject.

You can select the Autotype-WindowTitle from the Autotype section of each Entry settings. 
The setting is a List of Window's Title to search for a match.

The WindowTitle dropdown menu is filled with a list of currently open Window, alternatively you can insert a custom Window name or a RegEx to match your needs.

### Regular Expression (RegEx)

When using RegEx in window title you have to start and end the string with `//` (double slashes).  
For example `//Coconut//`

**Note**
 - `.*` -> means throw away everything
 - `()` -> means select the part inside the bracket
 - `(.*)` -> means select everything

#### Match every Window
You can match every Window Title with a blank string ` ` or with the RegEx `//(.*)//`

#### Match a Window or another
You can specify a list of Window Title by using the **or** (`|`) operator.  
For example `//Mozilla Firefox|Chrome//` will match the two browser Window so you can perform Autotype in both of them.
Alternatively you can add 2 Window Title to the List `//Mozilla Firefox//` and `//Chrome//` if you need to set up different sequence.

#### Match 2 string in a single Title
You can specify 2 different string to be matched in the Window Title like the **and** logic operator.
This can be achieved with the following RegEx. `//Part1.*Part2//`  

For example `//Github.*Login//` will match **only** the Github Login page and it wont match Twitter login page or Github homepage.

