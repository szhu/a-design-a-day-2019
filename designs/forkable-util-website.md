# Forkable Utility Website

## Background

There are numerous websites that allow the user to do small tasks:

<table><tr><td>

![image](https://user-images.githubusercontent.com/1570168/51652118-591f3c80-1f43-11e9-953c-b2398ed911ab.png)

<td>

![image](https://user-images.githubusercontent.com/1570168/51652271-e6fb2780-1f43-11e9-9b4a-6a4cb5463b9b.png)


<tr><td>

![image](https://user-images.githubusercontent.com/1570168/51652215-b74c1f80-1f43-11e9-8f6c-80994969bf16.png)

<td>

![image](https://user-images.githubusercontent.com/1570168/51652336-1873f300-1f44-11e9-930e-41287fd0e10c.png)

</table>

Each website, and the process of discovering it, is generally very heavy compared to the small task most users use it to accomplish. In addition, the websites all have different UIs, which imposes a learning curve.

## Idea

A website with no server-side code, containing a library of interfaces for accomplishing the above tasks.

Advantages:

- Eventually, this can be a one-stop shop for 90% of the small text-based (and related) tasks that people need to accomplish.

- The Facebook app is 300MB+ on most phones, yet many people install it even if they only use it sparingly. Even if the utility site became very function-rich, there is no way it would even approach that size.

- Versatile. It can be downloaded and used offline. Someone can package it into an app for non-technical users, if need be.

  - None of the above prevents this site from having server-side capabilities. For example, a server can be contacted for currency conversion rates. The key, though, even if we are offline or the server isn't working, all the other utilties on the site should work.

- Easy to improve: since the server-side files are static, just fork the repo, make your edits, test, and make a PR. Only a text editor, web browser, and Git are required.

