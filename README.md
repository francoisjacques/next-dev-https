# next-dev-https

This is a minimally modified next development server with support for self signed https certificates and console QR codes. It aims to ease the hassle of using your mobile device as your primary development target. Use local https to access all the APIs that are restricted to [secure contexts](https://developer.mozilla.org/en-US/docs/Web/Security/Secure_Contexts/features_restricted_to_secure_contexts).

I pretty much had a version of this script in all my work projects so i decided to make a package.

## Usage

Install `next-dev-https` from npm with any package manager into your existing next project. Run `next-dev-https` instead of `next dev` to use this server. It works identically to the regular next dev with two extra optional parameters:

- `--qr/-q` Print a phone scannable QR code of your dev server's local network url on startup and `q` or `Q` press.
- `--https/-s` Generate and use a self signed https certificate for the dev server.
- `--user-cert-dir/-d` A user-level directory containing a localhost.pem and localhost-key.pem files, relative to `os.homedir`  
### Example package json

```jsonc
{
 //...
 "scripts": {
   "dev": "next-dev-https --user-cert-dir .my-awesome-certs"
   //...
 }
 //...
}
```

_Tip: Don't use a port where you regulary host http stuff, your browser will remember the protocols for urls and get confused when you switch back and forth._

## Trusted certs?

You can use trusted certs located in a directory relative to your user directory using the argument `--user-cert-dir`. If generated locally, the authority must be add to your system's certificate autorities store.

## Turbopack?

Turbopack is not supported, it uses a custom rust server and looks to require changed binaries to use https. :(
