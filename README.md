# [uBO-R](https://github.com/gorhill/uBlock/wiki/Dashboard:-My-rules)
> [!warning]
> This requires [Advanced Mode](https://github.com/gorhill/uBlock/wiki/Advanced-user-features) to be enabled

## Profiles
AKA "User Types"

### Admin
For privileged (Administrator) accounts. These are the only users with (partial) `root`/`System` access, so they need **ABSOLUTELY MAXIMUM SECURITY** at the cost of convenience. Since admins don't need to browse many websites, the strict-blocking doesn't affect them much.

BTW, remember to disable JIT-compilation:
- MS Edge: Go to "Enhanced Security" (`edge://settings/privacy#SecureMode`)
- Moz Firefox: `about:config`, then search "jit". As a bonus, disable [Ion](https://wiki.mozilla.org/IonMonkey) and Wasm.
- G Chrome: CLI arg `--js-flags="--jitless"` (not persistent)

### User
An arbitrary average human user. They shouldn't be using "Hard-Mode", because literally any site they visit could break, and that's an inconvenience.

Most rules are "just-in-case", for the sake of future-proofing, and lack of information about the behavior of sites.

### Rx
My own personal rule-set. Designed for my needs, desires, and convictions.

## Modes

### std
Stands for "standard". It's meant to be used with minimal modifications, as it allows most of the typical content that the user will need.

### min
Minimal `noop`, max restriction. Meant to be modified in an additive way (by adding rules to "Temporary"), which gives more control to the user.
