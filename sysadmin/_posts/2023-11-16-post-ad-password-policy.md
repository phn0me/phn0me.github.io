---
title: "Active Directory - Password Policy"
---

### Did you know...
That Active Directory's [password policy](https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh994562(v=ws.11)#reference) doesn't enforce four out of four character varieties?

> The password must contain characters from three of the following categories:
> - Uppercase letters of European languages (A through Z, including diacritic marks, Greek, and Cyrillic characters)
> - Lowercase letters of European languages (a through z, sharp-s, including diacritic marks, Greek, and Cyrillic characters)
> - Base 10 digits (0 through 9)
> - Non-alphanumeric characters: !@#$%^&*_-+=\|(){}[]:;"'<>,.?/~
> - Any Unicode character categorized as alphabetic but not uppercase or lowercase, including characters from Asian languages.


### Password Policies

Depending on other settings, such as password length, this isn't inherently a bad policy.
However, enforcing only three of the four categories is not recommended.

In practice, this means passwords like `Password!` or `password123!` are allowed.
While `Password123!` would still pass if all four categories were enforced, that's a topic for another time.

Most users tend to prefer shorter passwords that barely meet the requirements in order to avoid the hassle of creating longer, more complex ones.

[xkcd](https://xkcd.com/936/) nailed it: we've forced users to use short, complex passwords that are difficult to remember but easy for computers to crack.

There’s an ongoing debate about whether short, complex passwords are better than their longer, simpler counterparts.
The answer likely lies somewhere in between.

A longer, memorable password with some complexity works best.
For example:

```1Guitar#6Strings#DroppedC```

These are the kinds of passwords I've found most effective:
Complex enough to thwart brute-force attacks, yet easy to remember and not too difficult to type.

The main issue remains: Active Directory, in its current state, doesn’t allow for more than three out of four character categories.

### Third Party Solutions

* **PAID** - [Specops Password Policy](https://specopssoft.com/product/specops-password-policy/) allows system administrators to bypass Active Directory’s native password policies using Group Policies.
  It offers features like checking compromised passwords, banning certain words based on word lists or regex, and automating notifications when passwords are compromised.

* **Open Source** - [Lithnet Password Protection](https://lithnet.io/products/password-protection) is similar to Specops Password Policy, but lacks some advanced features.
  Lithnet checks for compromised passwords using [Have I Been Pwned](https://haveibeenpwned.com) thats locally stored, and allows you to add custom word lists. It also supports regex-based banned word checks and provides a PowerShell module for automation.

**Note:** I am not affiliated with any of these companies.


### That's it?
Definitely not!

Assuming a threat actor has gained internal access to hashed passwords for offline cracking, the password's complexity becomes irrelevant. Once compromised, the hash can be cracked instantly, regardless of length or complexity.

But, of course, users never reuse their passwords, right?


### What can we do?
To improve password hygiene and assess vulnerabilities, you can perform your own password audits.

* ___Password Cracking___
    * [CrackMapExec](https://github.com/byt3bl33d3r/CrackMapExec/wiki/SMB-Command-Reference) can be used to download NTLM hashes from a domain controller.
    * [Hashcat](https://hashcat.net/hashcat/) with a [wordlist](https://www.weakpass.com) and [hashcat rules](https://github.com/stealthsploit/OneRuleToRuleThemStill) for password cracking.
    * By analyzing cracked passwords, you can identify useful patterns—such as whether users include their organization's name or the local sports team in their passwords.
* ___Specops___ offers a free, read-only [audit tool](https://specopssoft.com/product/specops-password-auditor/) to check for weak, reused, or compromised passwords.
* ___Educate___ users on proper password hygiene, including the importance of not reusing passwords. Help them help us by clarifying IT policies and offering guidance.
* ___Defense in Depth___: Layers upon layers of security. Implement 2FA, use password managers, and perform regular audits.
* ___Be Patient and Supportive___: Some users may not have the same technical expertise, but scolding them won't help. A patient and supportive approach fosters better results.
