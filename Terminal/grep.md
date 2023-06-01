# Comando `grep`

- `-a` o `--text`: este parámetro indica a `grep` que trate todos los archivos como archivos de texto, incluso si contienen caracteres nulos o binarios.
```shell
grep -a "pattern" file.txt
```

- `-b` o `--byte-offset`: este parámetro muestra la posición en bytes de cada coincidencia de patrón dentro del archivo.
```shell
grep -b "pattern" file.txt
```

- `-c` o `--count`: este parámetro muestra el número de líneas que contienen coincidencias de patrón.
```shell
grep -c "pattern" file.txt
```

- `-d` o `--directories`: este parámetro controla el comportamiento de `grep` al buscar en directorios. Puede ser `read` para buscar en directorios, `skip` para omitirlos o `recurse` para buscar de forma recursiva en subdirectorios.
```shell
grep -d recurse "pattern" /path/to/directory
```

- `-e` o `--regexp`: este parámetro permite especificar el patrón de búsqueda como una expresión regular.
```shell
grep -e "pattern1|pattern2" file.txt
```

- `-f` o `--file`: este parámetro permite especificar un archivo que contiene patrones de búsqueda, uno por línea.
```shell
grep -f patterns.txt file.txt
```

- `-H` o `--with-filename`: este parámetro muestra el nombre del archivo junto con la línea que contiene la coincidencia de patrón.
```shell
grep -H "pattern" file.txt
```

- `-h` o `--no-filename`: este parámetro omite el nombre del archivo en la salida.
```shell
grep -h "pattern" file.txt
```

- `-i` o `--ignore-case`: este parámetro hace que `grep` ignore las diferencias de mayúsculas y minúsculas en el patrón de búsqueda.
```shell
grep -i "pattern" file.txt
```

- `-J` o `--bz2decompress`: este parámetro permite a `grep` buscar en archivos comprimidos en formato bzip2.
```shell
grep -J "pattern" file.bz2
```

- `-L` o `--files-without-match`: este parámetro muestra el nombre de los archivos que no contienen coincidencias de patrón.
```shell
grep -L "pattern" *.txt
```

- `-l` o `--files-with-matches`: este parámetro muestra el nombre de los archivos que contienen coincidencias de patrón.
```shell
grep -l "pattern" *.txt
```

- `-m` o `--max-count`: este parámetro limita el número de coincidencias de patrón que se muestran.
```shell
grep -m 3 "pattern" file.txt
```

- `-n` o `--line-number`: este parámetro muestra el número de línea junto con la línea que contiene la coincidencia de patrón.
```shell
grep -n "pattern" file.txt
```

- `-o` o `--only-matching`: este parámetro muestra solo la parte de la línea que coincide con el patrón de búsqueda.
```shell
grep -o "pattern" file.txt
```

- `-v` o `--invert-match`: este parámetro muestra todas las líneas que NO coinciden con el patrón dado.
```shell
grep -v "pattern" file.txt
```

- `-A num` o `--after-context=num`: este parámetro muestra num líneas después de cada línea que coincide con el patrón de búsqueda.
 ```shell
 grep -A 2 "error" log.txt
```

- `-B num` o `--before-context=num`: este parámetro muestra num líneas antes de cada línea que coincide con el patrón de búsqueda.
```shell
grep -B 1 "warning" log.txt
```
  
- `-C[num]` o `--context=num` o `--before-context=num` y `--after-context=num`: este parámetro muestra num líneas antes y después de cada línea que coincide con el patrón de búsqueda.
 ```shell
 grep -C 2 "error" log.txt
 ```

- D o --dereference-recursive: este parámetro hace que grep siga los enlaces simbólicos al buscar en directorios de forma recursiva.

```shell
grep -rD "pattern" /path/to/directory
```

- E o --extended-regexp: este parámetro permite especificar el patrón de búsqueda como una expresión regular extendida.
```shell
grep -E "(pattern1|pattern2)" file.txt
```

- F o --fixed-strings: este parámetro indica que el patrón de búsqueda es una cadena literal y no una expresión regular.
```shell
grep -F "exact phrase" file.txt
```

- G o --basic-regexp: este parámetro permite especificar el patrón de búsqueda como una expresión regular básica.
```shell
grep -G "pattern" file.txt
```

- H o --with-filename: este parámetro muestra el nombre del archivo junto con la línea que contiene la coincidencia de patrón.
```shell
grep -H "pattern" file.txt
```

- J o --bz2decompress: este parámetro permite a grep buscar en archivos comprimidos en formato bzip2.
```shell
grep -J "pattern" file.bz2
```

- L o --files-without-match: este parámetro muestra el nombre de los archivos que no contienen coincidencias de patrón.
```shell
grep -L "pattern" *.txt
```

- M o --max-count: este parámetro limita el número de líneas que se muestran.
```shell
grep -M 10 "pattern" file.txt
```

- O o --only-matching: este parámetro muestra solo la parte de la línea que coincide con el patrón de búsqueda.
```shell
grep -O "pattern" file.txt
```

- R o --recursive: este parámetro hace que grep busque de forma recursiva en subdirectorios.
```shell
grep -r "pattern" /path/to/directory
```

- `s` o `--no-messages`: este parámetro evita que grep muestre mensajes de error o advertencia.
```shell
grep -S "pattern" file.txt 2>/dev/null
```

- U o --binary: este parámetro indica a grep que trate todos los archivos como archivos binarios, incluso si contienen caracteres imprimibles.
```shell
grep -U "pattern" file.bin
```

- V o --version: este parámetro muestra la versión de grep.
```shell
grep -V
```

- w o --word-regexp: este parámetro hace que grep solo coincida con palabras completas en lugar de subcadenas.
```shell
grep -w "word" file.txt
```

- `X` o `--line-regexp`: este parámetro hace que grep coincida solo con líneas completas que coincidan exactamente con el patrón de búsqueda.
```shell
grep -X "exact line" file.txt
```