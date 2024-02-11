# alpine-openhasp

[HomeAutomation Switchplate based on lvgl](https://github.com/HASwitchPlate/openHASP)

openHASP built from the [kuba2k2/openHASP](https://github.com/kuba2k2/openHASP) repository with fbdev and SDL2 frontends.

## Installation

There are prebuilt APK packages available in this repo (for `x86`, `x86_64`, `armhf`, `armv7` and `aarch64`). They are signed with the following public key:

<details>
<summary>Click to show public key</summary>

```
-----BEGIN PUBLIC KEY-----
MIICIjANBgkqhkiG9w0BAQEFAAOCAg8AMIICCgKCAgEAvrueY+eFZkILqfOsb8T8
oxJ1tfM57VtIPJnGZeuEJchyd6AHbG7CCErdtLMRI7eWXJlAU23erFj6Wp/2zC5x
XgfuE5ekMmq/8WwkvLYl9i9I/tgiFWklHkLAOsY8LkwtuQDeDEt3gMPFheY3uNaN
FMWXKYWmknsQM10IV28TgDPfMLbVh7LagFbsKLWang50N+eGiMwQi+N1fZ/rrpk/
Rco5opHpTOC1i+GTXCcVkuOisTFw741p7fFhWksgN7XZBwDXE472KLWV/he6mAqA
/PbWmZHQxCdL1NwYJS5v9+K/c2sRUGb0dcHjC0bf9etrEg4otY7iydwZnM180mpt
oMRxSLb63OFcfsNtJRu8+Wy/oZ28HzQeEqF9d7Z6o3OrXntoAqRneFNet/GMap5U
1fjDEh79X0sjcZuASTV8hb4VvXR9s8Drw/POnpYdX1wLDSRm+N4Z0CoJDP0+CxVr
y11wSJmgyqkrZRfNyyQBW6H+zL+Pu5F15nq75fUlhE0eoBTi38THGgoGQSikBsHG
UXNr4nUIenfq0fzEYSlPYG3kXe/8FSKvNjUCYhpbwBEmhQ/NRWRfqBnvRS6Si1wP
+glz4VsR26fyMr2uH4SPL5c//GIgdCBZgfYusQsZjnJZkWDD8C61ijxBt+7cA0Sg
FN0IX6Z7106y3qPUktG2f+cCAwEAAQ==
-----END PUBLIC KEY-----
```
</details>

Enable the APK repository from this GitHub repo:

```bash
echo "https://kuba2k2.github.io/alpine-openhasp" | sudo tee -a /etc/apk/repositories
# install the public key
sudo wget -O /etc/apk/keys/actions@kuba2k2.github.io-64b57843.rsa.pub https://raw.githubusercontent.com/kuba2k2/alpine-openhasp/master/actions@kuba2k2.github.io-64b57843.rsa.pub
# update repos
# APK should now show the "alpine-openhasp" repo
sudo apk update
```

Finally, install the packages:

```bash
# openHASP with fbdev frontend
sudo apk add openhasp-fbdev
# openHASP with SDL2 frontend
sudo apk add openhasp-sdl
```

## Usage

openHASP with fbdev frontend is available in the `openhasp-fbdev` service. It stores configuration in `/usr/share/hasp`. The default `config.json` should be edited first.

It can also be launched manually using `openhasp-fbdev` command. Note that the fbdev frontend may require the user to be a member of `video`, `input` and `tty` groups.

The SDL2 frontend can be launched using `openhasp-sdl` command. It requires a running X server. Optional `-W` and `-H` parameters specify the window size.

When launched manually, the configuration is stored in `~/.local/share/hasp/hasp`. This can be changed using the `-c` parameter.
