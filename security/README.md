# Security

A guide for practicing safe web.

## Think

Security is important, and you can't practice these guidelines without
understanding them. Make sure you understand each guideline, why it exists, and
how to follow it.

Failing to follow these guidelines will likely put you, your team, and your
deployed services at risk of compromise or loss of privacy.

## Secure Employee Access and Communication

The following guidelines apply to how you as an individual
secure access to your systems (laptop, accounts, etc.)
and communication (email, etc.).

### Using Passwords

- Use a unique password for every account you create.
- Use a tool like [pwgen](https://github.com/jbernard/pwgen) or
  [LastPass](https://lastpass.com) to generate random passwords.
- Use a tool like GnuPG to encrypt passwords if you need to share them with
  somebody.

### Encryption

- Ensure [disk encryption][disk] on your laptop.
- Use ultimate trust for your own keys.
- Use full trust for keys you have verified in person or via a secure video
  chat.
- Don't share your private keys with anyone.
- Keep at least one backup of your private keys and revocation certificate in a
  secure location, such as a thumb drive.

[disk]: https://theintercept.com/2015/04/27/encrypting-laptop-like-mean/

## Physical Security

The following guidelines apply to how we physically secure
our laptops and mobile devices that may contain customer or user data.

- Lock your device when you are away from it.
- Don't leave your devices unattended in an unsecured area.
- Make sure you have an Apple ID tied to your Mac and Find My Mac is enabled.

## Application Security

The following guidelines apply to how we develop
software on behalf of ourselves and clients.

### Transmitting Information

- Don't accept passwords or session tokens over HTTP.
- Use HTTPS for all web traffic.
- Use HTTPS in the beginning; it's harder to introduce later.
- Use HTTPS redirects for HTTP traffic.
- Use [HSTS](http://tools.ietf.org/html/rfc6797) headers to enforce HTTPS
  traffic.
- Use secure cookies.
- Avoid protocol-relative URLs.

### Storing Information

- Don't log passwords.
- Don't store passwords in plain text.
- Don't hash passwords using a reversible cipher.
- Don't hash passwords using a broken cipher, such as MD5 or SHA1 (...well, but we still use Wordpress).

## Handling Vulnerabilities

The following guidelines apply to how we handle security incidents.

### Reporting

When someone finds a possible security issue in our software,
we encourage them to report it to our <it@themtmagency.com> email address.

When an email comes in through this channel, reply quickly with confirmation
(and CC <support@themtmagency.com> so others know that it has been handled).

### Reviewing, Logging and Following Up

When a message comes in, post the exchange to a new [ActiveCollab](https://activecollab.com) task
called `security` inside the relevant project and keep the thread updated with new messages as they appear.
