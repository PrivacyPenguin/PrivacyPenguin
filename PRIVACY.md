# PrivacyPenguin Privacy Policy

Version 1.0 – effective October 6, 2026

PrivacyPenguin is made by Near Systems, the name under which the individual developer of PrivacyPenguin publishes it ("we", "us"). This policy
explains what happens to information when you use the PrivacyPenguin app (including its background service and
command-line tool, the "Software") and its GitHub page.

## The short version

- **The Software collects nothing about you and sends nothing to us.** No account, no sign-in, no telemetry, no usage
  statistics, no crash reports sent automatically, no advertising.
- **It makes one connection of its own:** an optional, weekly check on GitHub for a newer version. You can turn it off.
- **Everything else stays on your PC,** unless you choose a feature that uses an outside service (Private DNS, browser
  tracker blocking) or you open a link (support page, release page).

## 1. Information the Software keeps on your PC

To do its job, the Software stores the following **only on your computer**. We never receive it.

| What | Why | Where |
|---|---|---|
| The original values of settings it changed | So every change can be undone | `%ProgramData%\PrivacyPenguin` |
| Your chosen settings and after-update preference | To keep your choice after Windows updates | `%ProgramData%\PrivacyPenguin\choices`, `%LOCALAPPDATA%\PrivacyPenguin` |
| Change history | The History page | `%LOCALAPPDATA%\PrivacyPenguin` |
| Logs (what was changed and when, errors, Windows account and computer names) | Troubleshooting | `%ProgramData%\PrivacyPenguin\logs`, `%LOCALAPPDATA%\PrivacyPenguin\logs` |
| Update-check status (on/off, last check, newest version found) | The update check | `%ProgramData%\PrivacyPenguin\update.json` |
| Your previous DNS settings, while Private DNS is on | So turning it off restores them | `%ProgramData%\PrivacyPenguin` |
| A short note that PrivacyPenguin closed because of an error (time and error type), until the next start | To offer a support report once | `%LOCALAPPDATA%\PrivacyPenguin\last-crash.txt` |

The **Privacy dashboard** shows which apps recently used your camera, microphone, location or screen capture. It reads
this from Windows on your PC and doesn't store or send it anywhere.

Uninstalling with "undo everything" deletes the shared folder (`%ProgramData%\PrivacyPenguin`). Each Windows account's
own folder (`%LOCALAPPDATA%\PrivacyPenguin`: history, a copy of the choice, the app log) stays until you delete it.
Uninstalling without "undo everything" keeps both, so your settings and history are still there if you reinstall. You
can delete any of these folders at any time.

## 2. Connections the Software makes

### 2.1 Update check (optional, on by default)

About once a week, the PrivacyPenguin service asks GitHub (GitHub, Inc., owned by Microsoft) for the version number of
the newest PrivacyPenguin release. The request contains only what any web request contains: your IP address, the time,
and a technical identifier showing the Software name and version (for example "PrivacyPenguin/1.0.0"). It contains no
information about you, your PC or your settings. GitHub handles the request under the
[GitHub Privacy Statement](https://docs.github.com/site-policy/privacy-policies/github-general-privacy-statement).
We don't receive data about individual checks.

The Software never downloads or installs updates by itself; if there is a new version, it tells you and you decide.

**To turn it off:** About page → untick "Check for updates automatically". The Software then makes no connections at
all, unless you click "Check now".

### 2.2 Private DNS (off unless you turn it on)

If you turn on Private DNS, Windows sends your DNS lookups (the names of the websites and services your PC connects to),
encrypted, to Quad9, an independent non-profit DNS service based in Switzerland, instead of to your internet provider.
Quad9's handling of this data is described in the [Quad9 privacy policy](https://quad9.net/privacy/policy/). We don't
receive any of it. Turning Private DNS off restores your previous DNS settings.

### 2.3 Browser tracker blocking (off unless you choose it)

If you choose it, your browser installs the uBlock Origin Lite extension from its official store (Microsoft Edge
Add-ons or the Chrome Web Store). The download is between your browser and the store, under Microsoft's or Google's
privacy policies. The extension is made by others and has its own privacy policy. We don't receive any data from it.

### 2.4 Links you open

The support page, the release page and other links open in your web browser. What you do there (for example writing an
issue on GitHub) is governed by that website's privacy policy.

**Support reports.** "Report a problem" (and the offers after an error or a failed change) shows a support report:
PrivacyPenguin's and Windows' versions, which PrivacyPenguin settings are on, recent history, and the end of
PrivacyPenguin's logs. It contains no passwords, files or browsing data, and Windows account names, the computer name,
user folder paths and account IDs are replaced before you see it. **Nothing is sent:** you read the report, and only if
you save it and attach it to an issue does anyone else see it – and then it is public on GitHub.

## 3. GitHub page and downloads

There is no PrivacyPenguin website yet. PrivacyPenguin's page and downloads are on GitHub, which handles your
visit under the [GitHub Privacy Statement](https://docs.github.com/site-policy/privacy-policies/github-general-privacy-statement);
we only see GitHub's total download counts, not who visits or downloads. The PrivacyPenguin website, when it comes, will
use no cookies, no analytics and no tracking.

## 4. Paid features (Plus)

There are no paid features and nothing to buy yet. Before paid features (Plus) are sold, this section will describe how
purchases work and what information we receive, and the change will be announced as described in section 9.

## 5. What we never do

We don't sell, rent or share personal information; we don't show ads; we don't build profiles; and we don't use your
information to train AI models.

## 6. Children

The Software is not directed at children under 13, and we don't knowingly collect information from them.

## 7. Your rights

Because the Software keeps your information only on your PC, you control it directly: you can view, change or delete it
at any time (see section 1). We hold no information about you on our side. Once there is a private contact form or paid features, you will be able
to ask us to access, correct, export or delete what we hold about you. Depending on where you live (for example the European
Union, the United Kingdom, California or Washington), you may have further rights under data protection law, and you
can complain to your data protection authority. We will not discriminate against you for using these rights.

## 8. Security

The Software runs on your PC, stores its files in protected Windows folders (the shared folder can only be changed by
administrators), and you can check that the installer comes from us with the SHA-256 checksum in its release notes (PrivacyPenguin is not yet code-signed; a later release will be).

## 9. Changes to this policy

Changes are announced in the release notes of the version that brings them and on PrivacyPenguin's GitHub page, with the
date they take effect. The current policy is always on that page and linked from the app's About page. If you pay for
Plus, we'll also tell you by email at least 30 days before a change that affects your purchase.

## 10. Contact

Questions about privacy: the support page, https://github.com/PrivacyPenguin/PrivacyPenguin/issues (public; don't post personal information there). We hold
no personal information about you. A private contact form will come with the PrivacyPenguin website.
