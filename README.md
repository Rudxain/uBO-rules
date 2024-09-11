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
> - Moz Firefox: use `Securefox.js`, and uncomment [these options](https://github.com/yokoffing/Betterfox/blob/c5fca2dbf7289c8dbce901c040683f3cdfdd7926/Securefox.js#L1131-L1162)
> - G Chrome: CLI arg `--js-flags="--jitless"`.
> 	- Not persistent, unless added to the desktop shortcut: This can be done on Windows (Properties -> Shortcut -> Target) and any system that supports the [FD spec](https://specifications.freedesktop.org/desktop-entry-spec/latest/ar01s07.html)

### User
Any human user, usually my family or friends. They shouldn't be using "Hard-Mode", because literally any site they visit could break, and that's an inconvenience.

Most rules are "just-in-case", for the sake of future-proofing, and lack of information about the behavior of sites.

### Rx
My own personal rule-set. Designed for my needs, desires, and convictions.

## Syntax
[uBO doesn't support comments on dyn-rules](https://github.com/gorhill/uBlock/issues/333).

uBO auto-removes syntactically-invalid lines, and [`#` is unlikely to become valid](https://github.com/gorhill/uMatrix/issues/314#issuecomment-128793820), so this hack _works_... as long as each comment is placed on **its own line** (side-comments will turn the **whole** line into a comment), so be careful
