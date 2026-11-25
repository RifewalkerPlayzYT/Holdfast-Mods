# Easier Admin

**Created by llstarlessll (Discord)**

Easier Admin is a helper for **Holdfast: Nations At War** server and event admins. It adds an **Easier Admin** tab to the P menu with buttons for the jobs admins do by typing `rc` commands: handing out weapons, changing game settings for fun rounds, running saved command sets, sending broadcasts, quick slays and messaging a whole regiment. It also keeps a warning count for each player, highlights chat that needs an admin, and tags possible firing-in-charge (FIC) kills in the admin kill log.

It is built on [RyLib](https://thunderstore.io/c/holdfast-nations-at-war/p/Ryanlt/RyLib/), so it sits in the game's own menus and works alongside **AdminHelper** without overlapping.

> Easier Admin only sends normal `rc` commands (and admin chat, which only logged-in admins see). It does nothing unless the server has accepted your `rc login`, and players do not need it installed. Everything it does also reaches console players.

---

## Installing

**With r2modman (recommended)**
1. Open r2modman and pick **Holdfast: Nations At War**.
2. Search the online mods for **EasierAdmin** and click **Download**. r2modman also installs BepInEx and RyLib.
3. Start the game with **Start modded**.

**By hand**
1. Install [BepInExPack_Holdfast](https://thunderstore.io/c/holdfast-nations-at-war/p/HoldfastModding/BepInExPack_Holdfast/) and [RyLib](https://thunderstore.io/c/holdfast-nations-at-war/p/Ryanlt/RyLib/).
2. Copy `BepInEx/plugins/EasierAdmin/EasierAdmin.dll` into the same folder in your game.

---

## Getting started

1. Join a server where you are an admin.
2. Log in: open the console and type `rc login <password>`.
3. Press **P**. A new **Easier Admin** header tab appears, with five pages: **Weapons**, **Fun Settings**, **Admin**, **Players** and **Hotkeys**. Switch pages with the icon buttons at the top of the tab.

The pages only show after the server accepts your login.

---

## Weapons page

### Give a weapon
| Control | What it does |
| --- | --- |
| **Weapon** list | Pick the weapon the buttons hand out: muskets, rifles, carbines, blunderbusses, pistols, WW1 revolvers and rifles, swords, axes, pikes (pitchfork included), knives, clubs and joke weapons like the frying pan. |
| **Give to everyone** | Gives the chosen weapon to every living player on the server, whatever their player number. |
| **Take from everyone** | Takes the chosen weapon away from every living player. Click twice to confirm. |
| **Strip everyone** | Removes every weapon from every living player; they keep their fists. Click twice to confirm. |
| **Keep giving on respawn** | While on, every player who respawns gets the chosen weapon about a second later. Turn it off when the round is over. It only runs while you are in the server. |
| **Include bots** | Also gives weapons to bots. Off by default. |

Players who are dead when you click cannot receive a weapon (the game refuses it). Use **Keep giving on respawn** to catch them.

### Loadouts
Three saved sets of weapons. Type the weapon names, separated by commas, in **Loadout 1** to **Loadout 3**, then click **Give loadout to all**. Use the game's weapon names, for example `Spontoon_Pitchfork,Pistol_Land_Pattern_Pistol` (capital letters do not matter). A name the game does not know is skipped and you are told which one. Loadouts are saved on your PC.

### One player
Open a player in the P menu **Players** tab (or click a row in the admin **Kill Log**) and use the buttons Easier Admin adds:
- **Give weapon**: gives that player the weapon chosen on the Weapons page. Handy when someone spawned without a musket.
- **Give loadout 1**
- **Strip weapons**
- **Slay (reason 1, 2, 3)**: slays the player with the reason set on the Admin page.
- **Warn**: sends the player a warning and counts it (see Warnings below).
- **Kick (warnings)**: kicks the player once they have reached the warning limit; click it twice to confirm.
- **Watch in chat**: highlights everything this player says in chat. Click again to stop.

---

## Fun Settings page

### Game settings
Switches and sliders for the server settings used in fun rounds. Each change is sent to the server straight away (sliders send once you let go).

| Control | Server setting |
| --- | --- |
| Explosive firearms | `characterExplosiveFirearms` |
| Infinite ammo | `characterInfiniteFirearmAmmo` |
| God mode | `characterGodMode` |
| Fall damage | `characterFallDamageEnabled` |
| Allow firing | `allowFiring` |
| Allow artillery | `allowArtyFiring` |
| Run speed | `characterRunSpeed` (1 = normal) |
| Jump force | `characterJumpForce` (1 = normal) |
| Explosion size | `explosionScaleMultiplier` (1 = normal) |
| Explosion knockback | `explosionKnockbackForceMultiplier` (1 = normal) |
| Ragdoll force | `ragdollForceMultiplier` (1 = normal) |

**More game settings**

| Control | Server setting |
| --- | --- |
| Allow blocking | `allowBlocking` |
| Bullet drop | `characterWeaponFirearmApplyDrop` |
| Infinite range | `characterWeaponInfiniteRange` |
| Horse for everyone | `vehicleHorseForAll` (everyone spawns with a horse) |
| Force first person | `forceFirstPersonMode` |
| Weapon damage | `characterWeaponDamageScale` (1 = normal) |
| Walk speed | `characterWalkSpeed` (1 = normal) |
| Horse jump | `vehicleJumpHeightMultiplier` (1 = normal) |
| Cannon loading speed | `cannonLoadingSpeedMultiplier` (1 = normal; also rockets) |

**Reset to default** (click twice) sends `rc set default` and puts every switch and slider back.

**Apply all to server** sends every switch and slider exactly as shown. The game does not let mods read the server's current settings, so the page starts at the normal defaults each time you launch the game. If a round's config already changed something (for example god mode at the start of a fun round), the page will not show it: use **Apply all to server** or **Reset to default** to make the server match the page.

### Scheduled commands
Run something later without typing `rc delayed` lines.
1. Type the command in **Command (no rc)**, for example `broadcast CHARGE!`. Separate several commands with `;`.
2. Set **Delay (seconds)**.
3. Click **Schedule**. You can schedule several; **Cancel all** (click twice) clears them.

Scheduled commands run from your game, so they only fire while you are in the server.

---

## Admin page

- **Macros**: two saved sets of commands, run with one click or a hotkey. Separate commands with `;`.
  - Macro 1 (default "Go live"): `set characterGodMode false; set allowFiring true; broadcast LIVE!`
  - Macro 2 (default "All charge"): `ac 30`
- **Broadcasts**: three message templates. Edit the text, then click **Send**.
- **Quick slay reasons**: the reasons used by the **Slay (reason 1)**, **(reason 2)** and **(reason 3)** buttons on the player row and kill log. The player is slain and told why. Defaults: *Out of line*, *Firing before LIVE*, *Teamkilling*.

### Warnings
Click **Warn** on a player (player row or kill log). The player gets a private message such as *"Admin warning 2/3: Follow the event rules"*.
- **Share warnings in admin chat** (off by default): when you switch it on, each warning and kick is also posted in admin chat (`[EA] WARN 2/3 Name (#12): reason`), which only logged-in admins see. Every admin running Easier Admin then keeps the same count, so the whole team sees "3rd warning". Leave it off if your event host doesn't allow extra messages; your own count still works.
- When a player reaches the limit (**Warnings before slay / kick**, default 3), a box appears at the top right with **Slay**, **Kick** and **Dismiss**.
- Counts are kept for the night (they reset by themselves the next day) and survive restarting the game. **Show tonight's warnings** messages you the list; **Reset warnings** (click twice) clears it.
- **Warning reason** is the text sent with each warning.

### Chat alerts
Chat that needs an admin is highlighted in yellow and listed in a box at the top right for 25 seconds.
- **Alert words** (comma separated, capitals don't matter). Default: `admin, report, help, tk, teamkill, rambo, fic, hack, cheat`.
- **Watched players**: everything they say is highlighted. Use **Watch in chat** on a player row, or type names here.
- **Clear alerts** empties the box.

### FIC tags in the kill log
FIC (firing in charge) is when someone fires into a melee that their own side is in and kills someone. Easier Admin checks every firearm kill:
- the victim was an enemy, and
- a living teammate of the shooter was within **Melee range** (default 3 m) of the victim, and
- the shooter was at least **Shooter at least** (default 4 m) away, so close fights inside the melee don't count.

When all three match, the kill log row gets a red **[FIC?]** tag after the shooter's name, an alert appears at the top right (who shot whom, how far, and which teammate was in the melee), and the shooter's count for the round goes up. **Show FIC count this round** messages you the counts; **Reset FIC count** clears them.

It is a hint, not proof: it only sees kills (not misses or wounds), and it can only check players your game knows the position of, so it works best while you are spawned or spectating near the fight. Always check before you punish.

### Teamkill tracker
Every teamkill is counted per player for the night:
- the kill log row gets an orange **[TK 2]** tag after the killer's name (their 2nd teamkill tonight), and an alert shows who killed whom and how;
- at the limit (**Teamkills before warn / slay / kick**, default 3) a box at the top right offers **Warn**, **Slay**, **Kick** or **Dismiss**;
- only shots and melee count unless you switch on **Count artillery and explosions**;
- **Show tonight's teamkills** messages you the list; **Reset teamkills** (click twice) clears it. Counts reset by themselves the next day.

**Nothing is automatic.** Easier Admin never warns, slays, kicks or messages anyone on its own: the boxes only offer buttons, and you decide. The only message a button sends is the one it says (a Warn sends the warning to that player). **Kick (warnings)** on a player row asks you to click it a second time. Admin chat sharing is off unless you turn it on. The confirmation messages Easier Admin sends you are private to you and can be turned off in P menu > Mods > Easier Admin.

---

## Players page

- **Regiment messages**: type a **Regiment tag** (as players wear it, for example `ABC`) and a **Message**, then click **Message regiment** to send it privately to everyone wearing that tag. **Ask to swap sides** sends everyone in that regiment: *"<tag> please swap sides for the remainder of the event!!"*, with the tag filled in (for example *"ABC please swap sides for the remainder of the event!!"*). The game has no command to move players, so this asks them to switch.
- **Show team count**: a small box on screen with the number of living players per side, by class and by the biggest regiments.

---

## Hotkeys

Set your own keys in game: **P menu > Easier Admin > Hotkeys** page.

1. Click the action you want a key for.
2. Press the key. Hold **Ctrl**, **Shift** or **Alt** with it for a combination, for example `Ctrl + G`.
3. You get a private message confirming the new key. **Esc** cancels, **Backspace** clears the key. If no key is pressed within 10 seconds nothing changes.

| Action | Default key |
| --- | --- |
| Run macro 1 (Go live) | F9 |
| Run macro 2 (All charge) | F10 |
| Give the chosen weapon to everyone | F11 |
| Give loadout 1, 2 or 3 to everyone | not set |
| Turn keep giving on respawn on or off | not set |
| Strip everyone's weapons | not set |
| Send broadcast template 1, 2 or 3 | not set |
| Turn god mode on or off | not set |
| Turn allow firing on or off | not set |
| Show or hide the team count | not set |

- **Show my hotkeys** sends you a private message listing every key you have set. **Reset hotkeys** (click twice) puts the defaults back.
- Giving a key to a new action takes it off the action that had it, so two actions never share a key.
- Hotkeys only work while you are logged in as admin, and not while you are typing in chat.
- AdminHelper uses **F6**, **[** and **]**. You are warned if you pick one of them.
- Keys are saved in `BepInEx/config/com.llstarlessll.easieradmin.cfg` and can also be changed in r2modman's **Config editor**.

---

## Turning things off (P menu > Mods > Easier Admin)

Like AdminHelper, every part of Easier Admin can be switched off in its settings:

| Section | Switches |
| --- | --- |
| **Pages** | Weapons page, Fun Settings page, Admin page, Players page, Hotkeys (turning Hotkeys off also hides the Hotkeys page and stops every key) |
| **Player row and kill log buttons** | Give weapon, Give loadout 1, Strip weapons, Quick slays, Kill log actions |
| **Messages** | Confirm messages: the private messages Easier Admin sends you after each action |

Warnings, chat alerts, FIC tags and the teamkill tracker each have their own on/off switch on the **Admin** page.

Settings are saved in `BepInEx/config/com.llstarlessll.easieradmin.cfg` and can also be changed in r2modman's **Config editor**.

---

## Using it with AdminHelper

Easier Admin and AdminHelper both use RyLib, so their buttons share the player row, the kill log and the P menu without overlapping. AdminHelper covers rambo detection, AFK marking, spectate, bring, go to, revive and the minimap; Easier Admin does not repeat those.

---

## Troubleshooting

- **No Easier Admin tab**: you are not logged in. Type `rc login <password>` and wait for the server to accept it.
- **Buttons do nothing**: check you are logged in, and that the player is alive for weapon buttons.
- **A weapon is not given**: some weapons cannot be held together with others in the same slot; strip first, or try another weapon.
- **A loadout gives nothing**: check the weapon names; you get a message naming any the game does not know.
- **No confirmation messages**: they need you to be spawned or spectating in the server, and **Confirm messages** switched on in the Mods tab.
- **Logs**: `BepInEx/LogOutput.log` has a line for every action Easier Admin takes.

---

Easier Admin is made by **llstarlessll** (Discord). Feedback and bug reports are welcome on Discord.
