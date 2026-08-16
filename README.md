# 🇧🇷 criaAtalho

[🇺🇸 Read in English](#-criaatalho-english)

`criaAtalho` é um pequeno script em Bash para Linux que cria atalhos (`.desktop`) na área de trabalho a partir de uma URL, tentando automaticamente baixar e associar o favicon do site como ícone.

Este projeto foi criado **com fins didáticos**, como exercício prático envolvendo:
- shell script
- manipulação de strings
- criação de arquivos `.desktop`
- permissões de execução
- uso de ferramentas comuns do sistema Linux

---

## Motivação

No Ubuntu (e em outros desktops Linux), é possível criar atalhos arrastando a barra de endereços do navegador para o desktop, mas o ícone resultante costuma ser genérico.

Este script automatiza o processo, gerando:
- um arquivo `.desktop` funcional
- um nome baseado no domínio do site
- um ícone personalizado a partir do favicon, quando disponível

---

## Uso

```bash
criaAtalho https://exemplo.com
```

O comando cria um arquivo:

```
~/Desktop/exemplo.com.desktop
```

e tenta salvar o ícone em:

```
~/.local/share/icons/custom/exemplo.com.png
```

---

## Como o script funciona (visão técnica)

### 1. Validação de entrada

O script espera uma URL como primeiro argumento:

```bash
URL="$1"
```

Se nenhum argumento for passado, ele exibe uma mensagem de uso e encerra.

---

### 2. Extração do domínio

O domínio da URL é extraído usando `sed`, removendo o protocolo (`http://` ou `https://`) e qualquer caminho adicional:

```bash
BASE=$(echo "$URL" | sed -E 's#https?://##' | sed 's#/.*##')
```

Esse valor é usado como:
- nome do aplicativo
- nome do arquivo `.desktop`
- nome do arquivo de ícone

---

### 3. Download do favicon

O script tenta baixar o favicon padrão do site:

```bash
curl -fs "$URL/favicon.ico"
```

Se o download for bem-sucedido:
- tenta converter o `.ico` para `.png` usando `convert` (ImageMagick)
- se a conversão falhar, copia o `.ico` diretamente

Se não for possível obter o favicon, o script usa um ícone genérico (`applications-internet`).

---

### 4. Criação do arquivo `.desktop`

O atalho é criado diretamente via shell usando um *here-document*:

```bash
cat > "$DESKTOP_FILE" <<EOF
[Desktop Entry]
...
EOF
```

O campo `Exec` usa `xdg-open`, garantindo que a URL seja aberta no navegador padrão do sistema.

---

### 5. Permissão de execução

O arquivo `.desktop` é marcado como executável:

```bash
chmod +x "$DESKTOP_FILE"
```

Isso é necessário para que o ambiente gráfico reconheça o atalho como um aplicativo válido.

---

## Dependências

- `bash`
- `curl`
- `xdg-open`
- `sed`
- opcional: `ImageMagick` (para converter `.ico` em `.png`)

Sem o ImageMagick, o script continua funcionando, apenas usando o favicon original.

---

## Observações

- O script **não trata casos mais complexos**, como sites que definem favicon apenas via HTML.
- O foco é clareza e aprendizado, não cobertura total de edge cases.
- O código foi mantido propositalmente simples para facilitar leitura e experimentação.

---

## Licença

Uso livre para estudo, modificação e adaptação.

---

# 🇺🇸 criaAtalho (English)

[🇧🇷 Ler em Português](#-criaatalho)

`criaAtalho` is a small Bash script for Linux that creates desktop shortcuts (`.desktop`) from a URL, automatically trying to download and set the site's favicon as the icon.

This project was created **for learning purposes**, as a hands-on exercise involving:
- shell scripting
- string manipulation
- creating `.desktop` files
- execution permissions
- common Linux system tools

---

## Motivation

On Ubuntu (and other Linux desktops), you can create a shortcut by dragging the browser's address bar to the desktop, but the resulting icon is usually generic.

This script automates the process, generating:
- a working `.desktop` file
- a name based on the site's domain
- a custom icon from the site's favicon, when available

---

## Usage

```bash
criaAtalho https://example.com
```

The command creates a file:

```
~/Desktop/example.com.desktop
```

and tries to save the icon at:

```
~/.local/share/icons/custom/example.com.png
```

---

## How the script works (technical overview)

### 1. Input validation

The script expects a URL as its first argument:

```bash
URL="$1"
```

If no argument is passed, it prints a usage message and exits.

---

### 2. Domain extraction

The domain is extracted from the URL using `sed`, stripping the protocol (`http://` or `https://`) and any additional path:

```bash
BASE=$(echo "$URL" | sed -E 's#https?://##' | sed 's#/.*##')
```

This value is used as:
- the application name
- the `.desktop` file name
- the icon file name

---

### 3. Favicon download

The script tries to download the site's default favicon:

```bash
curl -fs "$URL/favicon.ico"
```

If the download succeeds:
- it tries to convert the `.ico` to `.png` using `convert` (ImageMagick)
- if the conversion fails, it copies the `.ico` file directly

If the favicon can't be retrieved, the script falls back to a generic icon (`applications-internet`).

---

### 4. Creating the `.desktop` file

The shortcut is created directly via shell using a *here-document*:

```bash
cat > "$DESKTOP_FILE" <<EOF
[Desktop Entry]
...
EOF
```

The `Exec` field uses `xdg-open`, ensuring the URL opens in the system's default browser.

---

### 5. Execution permission

The `.desktop` file is marked as executable:

```bash
chmod +x "$DESKTOP_FILE"
```

This is required for the desktop environment to recognize the shortcut as a valid application.

---

## Dependencies

- `bash`
- `curl`
- `xdg-open`
- `sed`
- optional: `ImageMagick` (to convert `.ico` to `.png`)

Without ImageMagick, the script still works, just using the original favicon file as-is.

---

## Notes

- The script **doesn't handle more complex cases**, such as sites that define their favicon only via HTML.
- The focus is clarity and learning, not full edge-case coverage.
- The code was kept intentionally simple to make it easy to read and experiment with.

---

## License

Free to use for study, modification, and adaptation.