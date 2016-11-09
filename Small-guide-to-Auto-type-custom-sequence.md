When using autotype you can set up a custom sequence that will be executed by KeePassXC when Autotype is performed.

A sequence is list of actions and characters. All the sequence is Case-Insensitive (but in this guide everything will be UpperCase).<br/>
Actions are keywords and keys placed inside curly bracket `{` and `}`.

An example of a key is `{ENTER}`.<br/>
An example of a keyword is `{USERNAME}`.<br/>

When you perform the Autotype, KeePassXC will ask you to unlock your database (if locked) and select the Entry you want to inject (if more than 1 are assigned to the same Window Title).
The key-press/characters will be injected in the focused input of the Front-Most Window.
 
For example a sequence like `Hello {USERNAME}{ENTER}` will result in the key-press of the `Hello ` string, the username's character from the selected Entry and the `ENTER` key.

### Keyword
#### {USERNAME}
This keyword will be replaced by the **username** field in the selected Entry

#### {PASSWORD}
This keyword will be replaced by the **password** field in the selected Entry

#### {TITLE}
This keyword will be replaced by the **title** field in the selected Entry

#### {URL}
This keyword will be replaced by the **URL** field in the selected Entry

#### {NOTES}
This keyword will be replaced by the **notes** field in the selected Entry

#### Custom Attributes
Currently Autotype don't support custom attributes.

### Special Keyword
#### {DELAY n}
This keyword will add a milliseconds delay **between actions**

For example: A string like `{USERNAME}{DELAY 1000}{ENTER}` will result in the Key-Press of the username's character, a delay of 1 second and finally the press of `ENTER` key.

#### {DELAY=n}
This keyword, inserted at the start of the sequence, will add a millisecond delay **between keypress**

This can be useful if the Autotype is typing too fast and some character are missing from the key-press

#### {CLEARFIELD}
This keyword will clean the input field

### Key

This is a list of all the possibile key you can use with Autotype:<br/>
`tab enter up down left right insert ins delete del home end pgup pgdown backspace bs bksp break capslock esc help numlock ptrsc scrolllock
add + subtract multiply divide ^ % ~ ( ) { }`