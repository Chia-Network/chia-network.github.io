---
lang: en
layout: post
title:  "Your Security is Important, A Guide"
date:   2021-05-28
author: "[Justin England](https://www.linkedin.com/in/justindengland), [Jonmichael Hands](https://twitter.com/LebanonJon), and [Roy Natian](https://www.linkedin.com/in/roynatian)"
---

Security is about making better choices. You can never be 100% secure, but you can always make better choices and be safer. Making better choices is especially important when it comes to protecting things of value, like the XCH in your Chia wallet!

There are two main areas to consider: securing your devices and your security habits

Keep this in mind: *Don’t trust anyone.* 

Assume malicious intent and verify things for yourself. Being reasonably paranoid when it comes to crypto is a good mindset. Your goal is to make things harder for the bad guys, and the steps below will help you do that. We're going to briefly go over the basics you need to do and then cover more advanced security practices in more detail.

## The Basics

### Securing Your Devices
* Keep your operating systems up to date
* Keep your router firmware up to date
* Use strong passwords for your computer login and other accounts
* Don't let people use your computer account. Use guest accounts

### Your Habits
* Do not trust anyone. Assume malicious intent, especially on the internet.
* Do not share your 24 word mnemonic key(s) with anyone. 
* When downloading Chia software, make sure you are downloading from the `chia.net` domain. 
* Avoid public Wifi, but if you use public Wifi, use a VPN
* Don't become a target: Don't boast about your winnings. Keep it to yourself.

##  Beyond the Basics

### Cold Storage
Your XCH is only as secure as your wallet. 

If your Chia wallet is not accessible electronically, then it becomes incredibly difficult to compromise and steal (basically impossible). We urge you to store your XCH in a *cold wallet*.

In broad strokes: You will create a wallet through a new 24 word mnemonic key on a secured computer not connected to the internet. Store the key in a safe place, like a safe, and not in a computer. You will set your XCH receive address to the wallet address associated with this new mnemonic key that's in cold storage.

Some methods of cold wallet storage include:
* writing your key on paper and storing it in a vault
* using a metal wallet, where you press your key into pieces of metal
* hardware wallets that are basically USB drives that store your key

One way of utilizing wallets in a safe way is this: Most of your XCH is stored in a cold wallet. You then have an accessible wallet (also known as a *hot wallet*) where you store a little bit of XCH for spending as you need it. 

Read more here: [Chia Keys Management](https://github.com/Chia-Network/chia-blockchain/wiki/Chia-Keys-Management#2-keys-farming-key--cold-storage-key)

### Beware of Spearphishing
Do you actually know the person you are talking to online is who they say they are? Do you know if the website you're on is legitimate? 

Spearphishing is a targeted attack where you are scammed in some way through legitimate-looking fake websites or message.
* When downloading Chia installers, verify the website you are on is `chia.net` and make sure there is a lock icon in the address bar.
* Anyone contacting you through email or messaging apps could be potentially trying to scam you. Beware of the links and files they send you. Double check who they say they are. You can read more about phishing and how to protect yourself [here](https://www.phishing.org/what-is-phishing). 

### Third-party Tools and Scripts
It is wonderful seeing the many community driven tools that have sprung up to help you on your Chia farming journey. These tools can be very useful, but they come with a risk. Unless you audit the code yourself, you really don't know if what you're using isn't going to steal your private keys. 

Even if you are using a popular tool that many say is safe, you don't know if the next version of the tool has had malicious code added to it.

### Remove Remote Access Tools
There are many stories of attackers using weaknesses with remote access tools like TeamViewer or Microsoft Remote Desktop to remotely infiltrate a computer and steal information. We highly recommend you turn off or uninstall such software on your computer. How to turn off remote access tools varies across operating systems so we leave it to you to research online and use the many guides out there to do this.

### Device Encryption
Encryption is one of the best tools in your arsenal. Enabling device encryption for your computers is highly recommended. If your computer ever gets lost or stolen, your data will remain inaccessible. Microsoft has a [support doc](https://support.microsoft.com/en-us/windows/turn-on-device-encryption-0c453637-bc88-5f74-5105-741561aae838) for this, macOS has [FileVault](https://support.apple.com/en-ca/HT204837), and Linux has a variety of methods for this that you can look up.




## What We Are Doing
* Verifying installer integrity: Implementing SHA-256 checksum for installer downloads.
* 

