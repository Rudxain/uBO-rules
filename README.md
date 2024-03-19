# [uBO](https://github.com/gorhill/uBlock)-R
These are just templates for general user types

## Profiles

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
My own personal rule-set. Optimized for my needs and desires.

## Modes

### std
Stands for "standard". It's meant to be used with minimal modifications, as it allows most of the typical content that the user will need.

### min
Minimal `noop`, max restriction. Meant to be modified in an additive way (by adding rules to "Temporary"), which gives more control to the user.
