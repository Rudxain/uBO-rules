# [uBO-R](https://github.com/gorhill/uBlock/wiki/Dashboard:-My-rules)
> [!important]
> This requires [Advanced Mode](https://github.com/gorhill/uBlock/wiki/Advanced-user-features) to be enabled

## Profiles
AKA "User Types"

### Admin
For privileged (Administrator) accounts. These are the only users with (partial) `root`/`System` access (AKA "sudoers"), so they need **ABSOLUTELY MAXIMUM SECURITY** at the cost of convenience. Since admins don't need to browse many websites, the strict-blocking doesn't affect them much.

> [!tip]
> remember to disable JIT-compilation:
> - MS Edge: Go to "Enhanced Security" (`edge://settings/privacy#SecureMode`)
> - Moz Firefox: `about:config`, then search "jit".
> 	- bonus: disable [Ion](https://wiki.mozilla.org/IonMonkey) and Wasm
> 	- bonus: use [`Securefox.js`](https://github.com/yokoffing/Betterfox)
> - G Chrome: CLI arg `--js-flags="--jitless"`.
> 	- Not persistent, unless added to the desktop shortcut: This can be done on Windows (Properties -> Shortcut -> Target) and any system that supports the [FD spec](https://specifications.freedesktop.org/desktop-entry-spec/latest/ar01s07.html)

### User
Any human user, usually my family or friends. They shouldn't be using "Hard-Mode", because literally any site they visit could break, and that's an inconvenience.

Most rules are "just-in-case", for the sake of future-proofing, and lack of information about the behavior of sites.

### Rx
My own personal rule-set. Designed for my needs, desires, and convictions.
