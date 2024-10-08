# Useful regex

## Find all duplicated lines
```shell
^(.*)(\n\1)+$
```

## Find duplicated lines including empty lines
```shell
((^[^\S$]*?(?=\S)(?:.*)+$)[\S\s]*?)^\2$(?:\n)?
```

## Delete duplicated lines
search  : `^(.*)(\n\1)+$`
replace : `$1`

## Select all text
- Select all text before the sign `'='`, regex: `^.*(?==)`
```shell
echo "activities.product.getAlias=product-getAlias" | grep -o '^.*='
```

- Select all text after `'='`, regex: `(?<==).*`
```shell
echo "activities.product.getAlias=product-getAlias" | grep -o '[^=]*$'
```

- Select all text before the sign `'='`, regex: `^.*(?==)`
```shell
echo "activities.product.getAlias=product-getAlias" | grep -o '^.*='
```

- Select all text after `'='`, regex: `(?<==).*`
```shell
echo "activities.product.getAlias=product-getAlias" | grep -o '[^=]*$'
```

* Select the first `7`  characters: `^.{7}`

## Date
- Select dates grater than specific hour. E.g 19h
```sh
echo "omnichannel.log" | grep -E '^.*\b(19|2[0-3]):[0-5][0-9]:[0-5][0-9],[0-9]{3}\b'
```