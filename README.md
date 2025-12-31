# [uBO-R](https://github.com/gorhill/uBlock/wiki/Dashboard:-My-rules)
> [!important]
> This requires [Advanced Mode](https://github.com/gorhill/uBlock/wiki/Advanced-user-features) to be enabled

> [!tip]
> If you just want to read text, I recommend a [TUI](https://en.wikipedia.org/wiki/Text-based_user_interface) web-browser such as [Lynx](https://lynx.invisible-island.net) or [`w3m`](https://en.wikipedia.org/wiki/W3m).
> Not loading a JIT-interpreter is much more efficient than not using it, same goes for audio-visual decoding+rendering.
>
> If you're on Android, [Termux has your back](https://github.com/termux/termux-packages/tree/69a05a2cfdcc5e30cbadbc0e884175175b9904e3/packages/lynx)! (`pkg i lynx`)
>
> gluegle (and other domains) only forces you to run JS if the browser supports it.

Tip: Don't just 📋CP. Remember to search commented-out rules and filters. They are optional, but can enhance the experience on specific devices and scenarios.

You can easily find them using these regexes (`*.ubo` & `*.abp` respectively):
```regex
^#\S.+
```
```regex
^!\S.+
```

## Profiles
AKA "User Types".

All file-names that have a stem ([`basename`](https://pubs.opengroup.org/onlinepubs/9799919799/utilities/basename.html) without extension) in common are considered to belong to the same profile. When you apply a profile to uBO, you are expected to use **all** files from said profile.

To check if a list of files are part of the same profile, use the `common_stem` fn:
```ts
const get_stem = (path: string) => {
	// `-1` is implicitly offset to `0`,
	// this is intentional.
	const basename = path.substring(path.lastIndexOf('/') + 1)
	const dot_i = basename.lastIndexOf('.')
	return dot_i == -1 ? basename : basename.substring(0, dot_i)
}

const common_stem = (paths: ReadonlySet<string>) =>
	[...paths].every((path, _, path_ls) =>
		get_stem(path_ls[0]) == get_stem(path)
	)
```
These fns are intended to be "normative", therefore, any bugs in them should be considered "specification mistakes" rather than "implementation bugs". I am 100% confident that both fns are bug-free!

### Admin
For privileged (Administrator) accounts. These are the only users with (partial) `root`/`System` access (AKA "sudoers"), so they need **ABSOLUTELY MAXIMUM SECURITY** at the cost of convenience. Since admins don't need to browse many websites, the strict-blocking doesn't affect them much.

> [!tip]
> Disable JIT-compilation:
> - [Moz](https://consumerrights.wiki/w/Mozilla) [Firefox](https://consumerrights.wiki/w/Firefox): use `Securefox.js`, and uncomment [these options](https://github.com/yokoffing/Betterfox/blob/c5fca2dbf7289c8dbce901c040683f3cdfdd7926/Securefox.js#L1131-L1162)
> - Chromium (e.g. [gluegle](https://consumerrights.wiki/w/Google) [chrome](https://consumerrights.wiki/w/Google_Chrome), [M$](https://consumerrights.wiki/w/Microsoft) [edging](https://consumerrights.wiki/w/Microsoft_Edge), ...): CLI arg `--js-flags="--jitless"`.
> 	- add it to the desktop shortcut (to make it persistent): This can be done on [winbloats](https://consumerrights.wiki/w/Windows) (Properties -> Shortcut -> Target) and any system that supports the [FD spec](https://specifications.freedesktop.org/desktop-entry-spec/latest/exec-variables.html)

### User
Any human user, usually my family or friends. They shouldn't be using "Medium-Mode", because literally any site they visit could break, and that's an inconvenience.

Most rules are "just-in-case", for the sake of future-proofing, and lack of information about the behavior of sites.

### Rx
> [!tip]
> Install [Libredirect](https://github.com/libredirect/browser_extension) and [YT-DLP](https://github.com/yt-dlp/yt-dlp)

My own personal rule-set. Designed for my needs, desires, and convictions.

## Syntax
[uBO doesn't support comments on dyn-rules](https://github.com/gorhill/uBlock/issues/333).

uBO auto-removes syntactically-invalid lines, and [`#` is unlikely to become valid](https://github.com/gorhill/uMatrix/issues/314#issuecomment-128793820), so this hack _works_... as long as each comment is placed on **its own line** (side-comments will turn the **whole** line into a comment), so be careful
