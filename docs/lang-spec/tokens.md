# Tokens in VastLang

Program written in VastLang is tokenized using the following rules:

 - Character `=` creates assign token.
 - Character `"` starts string token. Inside it can be following characters:
    - `"` - end of string
    - `\` - escape sequence - next character will be treated specially:
        - `\` - `\`
        - `"` - `"`
        - `'` - `'`
        - `n` - new line
        - `t` - tab
 - Character `:` starts label token. It takes all connected alphanumeric characters.
 - White characters don't produce any tokens:
    - space
    - tab
    - line feed
    - carriage return
 - If given fragment is one of [keywords](../keywords/), then keyword token is created.
 - Two slashes (`//`) start comment, which ends at line end. No token is created. Comments are ignored by interpreter.
 - Letter starts identifier token. It takes all connected alphanumeric characters.
 - Digits, plus and minus sign start number token. It takes all connected digit characters.