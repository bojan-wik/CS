#tools 

my_hotkeys.ahk
```
$^+v:: ; CTRL+SHIFT+V
ClipSaved := ClipboardAll ;save original clipboard contents
clipboard = %clipboard% ;remove formatting
Send ^v ;send the Ctrl+V command
Clipboard := ClipSaved ;restore the original clipboard contents
ClipSaved = ;clear the variable
return

^SPACE:: Winset, AlwaysOnTop, , A

^2:: ; CTRL+2
Send, test@test.com
return
/*
#IfWinActive Oracle SQL Developer
^PgUp:: ; CTRL+PgUp
Send +{F5} ; SHIFT+F5
Return
#IfWinActive
^PgUp::
Send ^+{Tab} ; CTRL+SHIFT+TAB
Return

#IfWinActive Oracle SQL Developer
^PgDn:: ; CTRL+PgDn
Send !+{F5} ; ALT+SHIFT+F5
Return
#IfWinActive
^PgDn::
Send ^{Tab} ; CTRL+TAB
Return
*/
```

---
- https://www.autohotkey.com/docs/Tutorial.htm
- https://medium.com/better-humans/how-to-setup-your-windows-global-hotkeys-in-10-minutes-becc40ff492
- https://www.itechtics.com/10-tools-to-always-on-top-any-app-in-windows-10/