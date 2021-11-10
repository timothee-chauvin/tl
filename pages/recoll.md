# recoll

- index:
`recollindex`
-> resulting index goes in ~/.recoll/xapiandb/

- solution to the following error: install the aspell-en package.
:2:index/indexer.cpp:415::ConfIndexer::createAspellDict: aspell buildDict failed: aspell dictionary creation command failed:
/usr/bin/aspell --lang=en --encoding=utf-8 create master /home/u/.recoll/aspdict.en.rws
One possible reason might be missing language data files for lang = en. Maybe try to execute the command by hand for a better diag.

- If starting to ignore something doesn't work, delete the database (rm -rf xapiandb) before re-indexing.
