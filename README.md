# noto-sans-mono-r0

Revert lower case "r" and number "0" to early version looking.

Based on new Noto Mono font "Noto Sans Mono",  
revert lower case "r" and number "0" to early "being removed Noto Mono" looking.  
https://github.com/googlefonts/noto-fonts/issues/1000 for more details.

R: Only lower case "r" is reverted.
R0: Both lower case "r" and number "0" are reverted.

## Download

Go to `Product` folder, download ttf files directly.

## Steps

- Open "Noto Sans Mono" with FontForge
- Open "Noto Mono" with FontForge,<br>
  but use File\Open from "Noto Sans Mono" window.<br>
  Otherwise clipboard copy paste between font may not work.
- Change settings under Noto Mono\Element\Font info\General<br>
  Ascent: 1638->800<br>
  Descent: 410->200<br>
  Underline Position: -205->-125<br>
  Height: 102->50<br>
  Em Size should auto convert to 1000, and OK to save
- Copy desired font from "Noto Mono" window to "Noto Sans Mono" window
- Change settings under Noto Sans Mono\Element\Font info\PS Names<br>
  Fontname: NotoSansMonoR0-Regular<br>
  Family Name: Noto Sans Mono R0<br>
  Name For Humans: Noto Sans Mono R0 Regular<br>
  Save, and generate new unique id for this font.
- Noto Sans Mono\File\Generate fonts<br>
  TrueType, 123456.ttf, then Generate.
