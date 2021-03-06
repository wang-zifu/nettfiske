[![Crates.io](https://img.shields.io/crates/v/nettfiske.svg)](https://crates.io/crates/nettfiske)
[![Build Status](https://travis-ci.org/wisespace-io/nettfiske.png?branch=master)](https://travis-ci.org/wisespace-io/nettfiske)
[![MIT licensed](https://img.shields.io/badge/License-MIT-blue.svg)](./LICENSE-MIT)
[![Apache-2.0 licensed](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](./LICENSE-APACHE)

# Nettfiske

Uses [certstream](https://certstream.calidog.io/) SSL certificates live stream to identify possible phishing domain names. It is inspired by [Phishing Catcher](https://github.com/x0rz/phishing_catcher).

## Usage

```rust
cargo run --release sample.json
```

### Example

```Console
[Nettfiske]  Fetching Certificates ...
Homoglyph detected youtuḅe.com (Punycode: xn--youtue-tg7b.com)
Homoglyph detected youtuḅe.com (Punycode: xn--youtue-tg7b.com)
Homoglyph detected whatsapp.com (Punycode: xn--hatsapp-h41c.com)
Homoglyph detected whatsapp.com (Punycode: xn--hatsapp-h41c.com)
Homoglyph detected twiṫter.com (Punycode: xn--twiter-507b.com)
Homoglyph detected twiṫter.com (Punycode: xn--twiter-507b.com)
Suspicious paypal.com-secure.warn-allmail.com (score 72)
Suspicious applêid.àpplê.com.iosets.com (score 65) (Punycode: xn--applid-lva.xn--ppl-8ka7c.com.iosets.com)
Suspicious facebook.com-verified-id939819835.com (score 69)
Suspicious appleid.apple.com.invoice-qwery.gq (score 75)
Suspicious instagramaccountverifica.altervista.org (score 69)
```

### Use Cases

Attempt to detect the use of Punycode and Homoglyph Attacks to obfuscate Domains. The homograph protection mechanism in Chrome, Firefox, and Opera may fail when some characters are replaced with a similar character from a foreign language.

Example:

* microsoft.com⁄index.html.irongeek.com
* microsoft.xn--comindex-g03d.html.irongeek.com

The slash symbol in the first url is not really a slash symbol at all. Also adding a SSL certificate can take few minutes and the user can feel safer with the locker next to domain.

Example, try to open the domain https://www.xn--80ak6aa92e.com/ on Firefox.