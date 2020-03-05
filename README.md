# @chiffre/crypto-box

[![NPM](https://img.shields.io/npm/v/@chiffre/crypto-box?color=red)](https://www.npmjs.com/package/@chiffre/crypto-box)
[![MIT License](https://img.shields.io/github/license/chiffre-io/crypto-box.svg?color=blue)](https://github.com/chiffre-io/crypto-box/blob/master/LICENSE)
[![GitHub Workflow Status](https://img.shields.io/github/workflow/status/chiffre-io/crypto-box/ci)](https://github.com/chiffre-io/crypto-box/actions)
[![Dependabot Status](https://api.dependabot.com/badges/status?host=github&repo=chiffre-io/crypto-box)](https://dependabot.com)

Lightweight serialization for TweetNaCl sealed box pattern.

## Formats

### Keys

TweetNaCl box key pairs are serialized using base64url, without trailing padding,
and prefixed with an identifying tag:

```
TweetNaCl box key pair:
Public key: pk.Oq5P4CKFp8FStZr6EfbHzkX53LkJTXNCqqHdm6djFhk
Secret key: sk.LY6NqZ_oEnlgkv-plSldGgHvXmtqHqlnkI5JSTIC7I0
```

### Messages

We use the sealed box pattern, where an ephemeral key pair is used for
encrypting every message. The ephemeral public key is sent as part of the
message, along with the nonce used for encryption and the ciphertext.

Example:

```
v1.naclbox.Eu6k3DshffqkRnqhtCFfZA4SCzgrxqXX6GeY1LbBZT0.utf8.LQ6atta_ET_-jLN2aLpKNIa35bDhxRum.ivrW2XNVK0_5Fc27oZpG3_onzX2U4Gg52oTbcEhN
```

The various parts are separated by a dot `.`:

| Part                 | Value                                         |
| -------------------- | --------------------------------------------- |
| Version identifier   | `v1`                                          |
| Algorithm            | `naclbox`                                     |
| Ephemeral public key | `Eu6k3DshffqkRnqhtCFfZA4SCzgrxqXX6GeY1LbBZT0` |
| Message encoding     | `utf8`                                        |
| Nonce or IV          | `LQ6atta_ET_-jLN2aLpKNIa35bDhxRum`            |
| Ciphertext           | `ivrW2XNVK0_5Fc27oZpG3_onzX2U4Gg52oTbcEhN`    |

Ephemeral public key, nonce and ciphertext are all base64url encoded,
with optional trailing padding `=` characters.

## License

[MIT](https://github.com/chiffre-io/crypto-box/blob/master/LICENSE) - Made with ❤️ by [François Best](https://francoisbest.com).
