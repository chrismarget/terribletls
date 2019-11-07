# terribletls
Go 1.13's TLS library butchered to include terrible ciphers. Do not use.

I needed a TLS library with TLS_RSA_EXPORT_WITH_RC4_40_MD5 and TLS_RSA_WITH_RC4_128_MD5, so that's what this is.

MD5 doesn't have a ConstantTimeSum(), but TLS1.0+ require it, so that's butchered in too. Is it O(1)? I have no idea.

Finally, I had to rip out some internal calls. The result is that unlike with the normal library, a terribletls.Config{} structure cannot have a nil CipherSuites list. You must specify the suites you want.

Thank you @stephen-fox for working through this with me.
