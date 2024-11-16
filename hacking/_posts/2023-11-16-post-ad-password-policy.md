---
title: "Active Directory - Password Policy"
tags:
  - sysadmin
---

### Did you know...
That Active Directory's [password policy](https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh994562(v=ws.11)#reference) doesn't enforce four out of four character varieties?

```
 The password contains characters from three of the following categories:
 - Uppercase letters of European languages (A through Z, with diacritic marks, Greek and Cyrillic characters)
 - Lowercase letters of European languages (a through z, sharp-s, with diacritic marks, Greek and Cyrillic characters)
 - Base 10 digits (0 through 9)
 - Nonalphanumeric characters: ~!@#$%^&*_-+=`|(){}[]:;"'<>,.?/
 - Any Unicode character that is categorized as an alphabetic character but is not uppercase or lowercase. This includes Unicode characters from Asian languages.
````

Depending on other settings, such as password length, this in of itself isn't bad.
However it's not recommended to only enforce three out of four requirements.

In practice, this means that passwords such as ```Password!``` or ```p4ssword!``` is allowed.

Since the majority of users tend to lean more towards having a shorter password i order to avoid <*insert reason here*> when having a longer, complex password.

There are discussions whether or not short complex passwords are better than their longer, less complex counterparts.
