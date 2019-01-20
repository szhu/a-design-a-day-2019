# User-Friendly Password Rejection

## Background

In most modern computer computer and phone operating systems, I get penalized with a delay after entering an incorrect password. This delay generally increases with each incorrect attempt, resetting after I finally enter the correct password.

A major goal of this design is to make brute-forcing passwords impossible (in software, at least) while not giving a large penalty to incorrect attempts resulting from typos.

Under a naive implementation of the system, if I make the same typo twice in a row, I get hit the same penalty. The penalty doesn't make sense -- a hacker who brute-forces passwords (or who tries a few from a list) won't ever need to re-enter the same password, since it can't help them. On the other hand, real account owners (👋), in their attempt to recite the long, complex passwords the security community loves to recommend, will often run into this situation.

The same situation applies to online passwords. When you enter the wrong password too many times -- even if you've only been entering the same password repeatedly -- the website will typically lock you out, requiring either for you to wait an amount of time or for you to reset your password.

As another example of password-entering frustration, some antiquated online password systems disallow certain characters when you set them, requiring you to set a password especially easy for you to forget. For example, if you were making an account on `dmv.ca.gov` ([which requires that passwords contain no spaces, no lie](https://www.dmv.ca.gov/portal/dmv/detail/SelfHelp/faq)), you might use your password generator to suggest a memorable password like `Correct horse battery staple!`. However, you can't use that password as-is! You have to manually modify it, perhaps into `Correcthorsebatterystaple!`. This becomes harder for you to remember, since now, out of all of your passwords for your different sites, there is one that is structured significantly differently than the others. Even worse, the actual login page at `dmv.ca.gov` of course won't remind you that spaces are not allowed in passwords -- it will just keep rejecting all of your password attempts containing spaces, and then lock you out.

## Idea

Solutions for the above include the following:

- If the same incorrect password is entered multiple times within the same short timeframe\*, recognize that it's a user who isn't sure if they mistyped. It won't be a hacker, who will probably use a more reliable method of password entry (automated, or at least copy/paste). Don't add an extra penality for subsequent occurrences of the same incorrect password.

- If the user typed the same incorrect password twice in a row within the same short timeframe\*, let them know so that they're aware that they have entered the password they intended and that it is incorrect. A hacker has more accurate password entry, and so will always know if they've entered the same password twice anyway.

- On a public website, if there are password requirements visible to the user when they are setting a password, the same set of requirements (at least the uncommon ones) should be visible to the on the login page. Hackers will already be able to see these requirements when they try to make an account themselves.

\* The first two solutions have a security implication: If the user leaves the computer without logging out and a hacker attempts to type another at the same computer, the hacker can test whether their password is the same as the incorrect password the user just typed. At first glance, this doesn't seem like a glaring hole, and can be mitigated by having the "short timeframe" reset timer mentioned above.

There is one principle that encompasses all of these: If a penalty for incorrect password entry doesn't penalize hackers, then it shouldn't exist.

