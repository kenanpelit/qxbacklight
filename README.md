# qxbacklight

A bash script for setting the brightness with `xbacklight` **q**uickly.

#### Dependencies

* xbacklight

#### Installation

1. Clone this repository (`https://github.com/spcmd/qxbacklight.git`)
2. Copy `qxbacklight` to somewhere in your `$PATH` (for example: `~/bin`) or copy wherever you like, then give the full path to the script when using it.
3. Make it executable (for example: `chmod +x /path/to/qxbacklight`)
4. Open the script with a text editor and configure the options (see `Configurable Options` and the detailed comments in the script).
5. Create keybinds for the `qxbacklight` commands (see `Commands`)

#### Commands

* `qxbacklight --help`  Help & basic information.
* `qxbacklight --up`  Increase brightness.
* `qxbacklight --down`  Decrease brightness.
* `qxbacklight --default`  Set brightness value to default.

#### Configurable Options

**Strongly recommended** to configure these options for yourself! 
<br>I left my values as a default (for reference: I'm using a Notebook with LED LCD display, which is very bright, so my values are relatively low).

* `DEFAULT_BR=18` Default brightness (in percentage).
* `STEP_AMOUNT=2` Decrease/increase brightness steps (in percentage).
* `NOTIFY="yes"` Send notification when setting the brightness.

**Notes:**

* Use `xbacklight -get` command to get the current brightness value, so you can set it at `DEFAULT_BR` as a default. 
* Since `xbacklight -get` returns a floating point number (e.g. `17.989757`) you should *round* this value to make an integer (e.g. `18`), and use this number as a default (`DEFAULT_BR`)
* `STEP_AMOUNT` will be added (increase/brigtness up) or substracted (decrease/brigtness down) from the current brightness value.
* The `NOTIFY` option works as a feedback (with `notify-send` command): it shows the new brightness value after setting the brightness. If you don't want a notification, just leave it empty (`NOTIFY=""`).

#### Example keybinds for Openbox

If you are using Openbox as a Window Manager, you can copy&paste these keybinds below into the Openbox key configuration file (`~/.config/openbox/rc.xml`), then reconfigure or restart Openbox (`openbox --reconfigure` or `openbox --restart`).

```html
<keybind key="C-W-Left">
    <action name="Execute">
        <command>qxbacklight --down</command>
    </action>
</keybind>
<keybind key="C-W-Right">
    <action name="Execute">
        <command>qxbacklight --up</command>
    </action>
</keybind>
<keybind key="C-W-KP_0">
    <action name="Execute">
        <command>qxbacklight --default</command>
    </action>
</keybind>
```
**Notes:**

* Make sure you configure the keybind keys for yourself.
* If you didn't copy `qxbacklight` to somewhere in your `$PATH` (see `Installation`), then you need to edit the `<command>` lines by setting the correct path to the script (for example: `<command>/path/to/qxbacklight --up</command>`)