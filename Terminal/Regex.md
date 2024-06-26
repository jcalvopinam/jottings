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

