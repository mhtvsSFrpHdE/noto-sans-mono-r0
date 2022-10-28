## Project

Some font were created long time ago (2019), and related project file was lost.  
But a `README.md` contains font modify steps were recovered from a hard drive.

## Steps of `Noto Sans Mono`

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
  TrueType, `NotoSansMonoR0-Regular.ttf`, then Generate.
