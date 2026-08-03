The following code was used in Windows Power Shell on [[2026-07-06 the theme for the day is necklines]] on 26 photos taken yesterday. Their file name was in the format 20260705_163158. I first moved them to my content > images folder in obsidian, and I wanted their name to be 2026-07-05_Mårdselefors_163158 (and additional numbers for the other photos). So I spoke to CoPilot, and it gave me this code:
````
Get-ChildItem 20260705_*.jpg | Rename-Item -NewName { $_.Name -replace '^(\d{4})(\d{2})(\d{2})_(\d+)', '$1-$2-$3_Mårdselefors_$4' }
````
saying that:
- the first bit `Get-ChildItem 20260705_*.jpg` is the command to select the .jpg files starting with yesterday's date,
- the second command `| Rename-Item` tells it that the selected files are to be renamed
- this part `$_.Name` means "the current file name"
- and `-replace '^(\d{4})(\d{2})(\d{2})_(\d+)'` divides each file names into groups. The first group (which becomes `$1`) has four digits, the second group  (which becomes `$2`) two digits, the third group  (which becomes `$3`) two digits, then the underscore, and finally the fourth group (which becomes `$4`) has the remaining digits:

| Group | Example Value |
| ----- | ------------- |
| $1    | 2026          |
| $2    | 07            |
| $3    | 05            |
| $4    | 163158        |
- the next bit `, '$1-$2-$3_Mårdselefors_$4'` adds the dashes between the groups and the name Mårdselfors before the unique bit of the file name (group `$4`).

# edit this one for next time:
````
Get-ChildItem 20260707_*.jpg | Rename-Item -NewName { $_.Name -replace '^(\d{4})(\d{2})(\d{2})_(\d+)', '$1-$2-$3_loppis_$4' }
```