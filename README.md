# Auth.GG Encryption Bypass PoC

**Tutorial Video:** https://youtu.be/LtiPOj6DuAg?t=36

**Credits:** https://keyauth.cc and [@CabboShiba](https://github.com/CabboShiba?tab=repositories)
<br>
<br>
Due to poor implementation of AES encryption within auth.gg, all programs, **including obfuscated ones** are able to be exploited to login **without** a valid user account.

No copyright has been infringed by this repository. My PoC was made using clean-room design. No property of auth.gg was modified in any of this process. System functions that don't belong to auth.gg were changed, that's all.

Additionally, the auth.gg c# code was stolen from a competitor named safeguard.gg, when the auth.gg owner paid someone to leak its source code and deface the website with an auth.gg advertisement https://archive.is/6rcmf. Later Outbuilt stole the code and published it https://archive.ph/GNIu4

## Open-source

All files are open-source. Feel free to download and host yourself.

You can host for free on https://www.000webhost.com/

## Alternatives to auth.gg

You could use my service https://keyauth.cc. We take privacy very seriously, hashing emails in addition to the standard practice of hashing passwords. The code is all open-source as well.

Nobody has or will be able to develop a bypass like this for KeyAuth, or cAuth - the one I mention below. The encryption key is never sent in the request, so you can't use HTTPDebugger to bypass. As long as the program developer obfuscates, string encrypts, adds integrity checks; the chance of issues are very slim.

Another open-source choice would be https://github.com/fingu/c_auth

## How is this different than other bypasses?

Typically, when people make bypasses. They only work on unprotected applications. They modify the direct program to skip over login. They're typically made by people with little knowledge looking for attention they don't deserve.

This bypass is different because it only modifies a system function. You can't add protection to a system function, since that's not your code. The API of auth.gg is insecure for sending the decryption key along with the encrypted data.

Unlike other bypasses, obfuscation and memory integrity checks will not solve the problem. Neither will re-writing the client code. The only solution must be done on the server-side API.

If auth.gg had a secure API, then the typical bypass would not be their fault. it would be the fault of the programming customers who didn't obfuscate or add any protection code.

Hopefully this makes a clear distinction. authentication services are not responsible for making sure your program can't be tampered with. they are however responsible with making sure the HTTP requests to their server can't be tampered with. auth.gg fails to do this by including the decryption key plain-text in the request.

## C# aka CSHARP

> **Warning** Saying "Update available"?
> By default I have the version set to 1.0, which some programs may differ. In this case, try either closing HTTP Debugger while starting or [download the source](auth.gg-Encryption-Bypass-PoC/tree/main/csharp/server) and change the version

Watch the YouTube tutorial video here: TBA

Download the ZIP file in Releases

Download HTTPDebugger https://httpdebugger.com/download_pro.html

Import the `HTTP Debugger Settings.xml` file into HTTPDebugger

![image](https://user-images.githubusercontent.com/83034852/234408208-0b6b4bc0-cba8-4c06-b0d8-a550a3168e4a.png)![image](https://user-images.githubusercontent.com/83034852/234408221-b081cab0-4b4a-47df-9fd5-31c70c0e2d95.png)


Drag the program using auth.gg onto `harmony-ssl-hook.exe`. If the program using auth.gg has DLL files it requires, you should place all those files within the folder that `harmony-ssl-hook.exe` is in.

Now, as long as you kept HTTPDebugger open, you should be able to login with any random username/password/license key.

## C++

Watch the video here https://files.catbox.moe/ju42i7.mp4
