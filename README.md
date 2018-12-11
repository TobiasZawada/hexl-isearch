`hexl-isearch-mode` complements `hexl-mode`.
It puts an entry "Hexl Isearch Mode" into the "Hexl" menu.

That menu item (de-)activates the minor mode `hexl-isearch-mode`. If you activate that mode isearch searches in the binary data instead of the hexl buffer.

The search string is read with read. So all escape sequences for lisp strings do work. As an example you can search for `\x0a\x0d` or `\^M\n` to search for dos line ends.
