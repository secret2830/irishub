# iris tendermint show-address

## Description

Shows this node's tendermint validator consensus address

## Usage

```
iris tendermint show-address <flags>
```

## Global Flags

| Name,shorthand        | Default        | Description                                 | Required | Type   |
| --------------------- | -------------- | ------------------------------------------- | -------- | ------ |
| -e, --encoding string | hex            | String   Binary encoding (hex\b64\btc ) | False    | String |
| --home string         | /root/.iriscli | Directory for config and data               | False    | String |
| -o, --output string   | text           | Output format (text\json)                 | False    | String |
| --trace               |                | Print out full stack trace on errors        | False    |        |

## Examples

### Show Address of Your Node

```shell
iris tendermint show-address --home=<path_to_your_home>
```

The sample output could be:
```
ica1jhax359kz6hm70swxpxumpgkaglr7yq8h03kv3
```

The output is encoded in Bech32, to read more about this encoding method, read [this](../../features/basic-concepts/bech32-prefix.md)
