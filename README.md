# vrchat-setup
Tips, tricks and notes for the best possible VRChat experience

## Reccomended

### UI

In general, 2D interface elements seem to toggle some switch in my brain that changes it from 'I'm in a place' to 'I'm looking at a screen of a place', so I'm a firm believer in hiding them until you need them. VRChat has gotten better about this recently, but there's still some holes.

#### Nametags

Ideally, name tags could be hidden for friends or faded out over time, reappearing when a friend switches avatars. In the mean time it's a good idea to simply disable them, popping them back open if you need a reference. VRC allows you to do this in settings, and the setting sticks.

#### HUD

Unfortunately, there's no such option for the always-on HUD, which will permanently diplay a microphone icon in the corner of your eyeball. If you want to disable this consistently, I've created a quick AutoHotKey script:

```
Loop
{
        WinWait, ahk_exe VRChat.exe
        Sleep, 20000
        WinActivate, ahk_exe VRChat.exe
        Sleep 100
        Send {Ctrl down}
        Sleep, 30
        Send {Y down} ; will be 'H down' for most people
        Sleep, 30
        Send {Y up}{Ctrl up}
        Loop
        {
            Sleep, 5000
            IfWinNotExist, ahk_exe VRChat.exe
            {
                break
            }
        }
}
```

Compiling this and placing it in your startup directory (Windows+R, 'shell:startup') will cause it to start automatically.

##### But what about invites?

You can get them back (and more!) by using VRCX: https://github.com/pypy-vrc/VRCX/

Simply enable notifications and the SteamVR overlay. While you're at it, enable online/offline notifications for VIPs (faved friends) and join/leave notifications for friends. No more accidentally abandoning someone at the front of a huge map!

## Optional

You can install https://github.com/fholger/vrperfkit for any GPU. Instead of the default settings, I would suggest setting the supersampling to 1.0 (off) and enabling CAS (contrast-adaptive sharpening). It will add a degree of grainyness/aliasing, especially to thin things like lasers, but at a huge boost in visual clarity.
