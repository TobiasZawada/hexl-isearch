`hexl-isearch-mode` complements `hexl-mode`.
It puts an entry "Hexl Isearch Mode" into the "Hexl" menu.

That menu item (de-)activates the minor mode `hexl-isearch-mode`. If you activate that mode isearch searches in the binary data instead of the hexl buffer.

The search string is read with read. So all escape sequences for lisp strings do work. As an example you can search for `\x0a\x0d` or `\^M\n` to search for dos line ends.

Consider a file containing the byte sequence `\x12\x01`. When you input `\x12` (hex-number 12 which is 18 in decimal) as search string you start with the partial input `\x1` which is also valid and corresponds to the hex number 1. When arriving at this partial input isearch already searches for `\x01` and ends up behind `\x12`. When you input the character `2` isearch continues its search from the position of `\x01` and fails.

That effect is avoided by `hexl-isearch`. It interprets `\x1` as invalid partial input. Only hex numbers with two digits are valid. When you input `\x1` isearch stops and waits until you input the second digit. After you enter `\x12` isearch continues and finds the right match at the beginning of the file.

For the same reason three digits are required for the input of octal numbers such as `\012` at the isearch prompt.


