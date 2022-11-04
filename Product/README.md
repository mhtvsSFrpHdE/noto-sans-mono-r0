# Product

## Mono

Normal Mono font, if you only need English font,  
or your IDE supports custom fallback font, they are fine.

## FakeMono

Some IDE only allows you to select one font,  
if a character is not covered by this font,  
operating system will use fallback font to draw them.  
If you don't like the font provided by operating system,  
people usually combine two different fonts together to create a new one,  
and it's never a simple thing to do.

Windows does support custom fallback font, but there are limitations.

### TTF only

Windows [FontLink](https://learn.microsoft.com/en-us/globalization/input/font-technology) only support TTF fonts,  
not even TTC, at least Google Noto TTC is not supported (Windows 10 22H2).

If a not supported font format is used,  
the system may bluescreen fail or show incorrect font render result.  
Goto `Material` folder, there is a tutorial about how to convert from OTF to TTF.

### Mono and Non-Mono

In theory, you can combine `Noto Sans Mono R0` and `Noto Serif CJK SC Medium` while programming,  
they look pretty beautiful in my experience.  
However, because `Noto Sans Mono R0` is technically a Mono font,  
you can only specify another Mono font as fallback in registry,  
which `Noto Serif CJK SC Medium` is not a Mono font.

Google Noto's `Noto Sans Mono CJK SC` is not the solution,  
this font is challenging my tolerance in aesthetic.  
On another hand, `Noto Serif Mono CJK` is not provided yet.  
Also, the current Mono implemented by compressing English Latin characters to 1/2 wide of CJK.  
Such behavior is bad for programming.  
And in programming, CJK is usually not important to be mono (mostly comments).

Noto Sans Fake Mono series font is created for this situation.  
It does look like Mono font, but technically, it's not Mono.  
This solution allows using any of your local language fonts as English font fallback,  
without having to modify the installed font file.  
The result is to utilize full wide of mono English latin and does not require CJK to be mono.

### Usage

Install NotoSansFakeMono ttf and convert one of the fonts you wish to use to ttf format,  
install that ttf to override your existing otf font,  
you may need to uninstall the otf one first.  
This is because Windows only support ttf as fallback font.  
Otherwise you get a bluescreen to fail to boot when using otf.

Choose one of the demo reg file from FontLink folder, import into your registry,  
this can tell Windows to use "Noto Serif CJK SC Regular" (for Mactype),  
or "Noto Serif CJK SC Medium" (for Windows native Cleartype) as fallback font.

You can then edit them to another font **after** import reg file:  
Navigate to `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\FontLink\SystemLink`,  
and find "Noto Sans Fake Mono".  
Notice that `Fake Mono`, `Fake Mono R`, `Fake Mono R0` are three different.

The `136,96` is used to match the size between font and its fallback.  
`128,96` is default value, imagine 128 is the fallback font size, adjust it as needed.  
For example, when use `Noto Sans Fake Mono` with `Noto Serif CJK SC Medium`,  
I change to 128 + 8 = 136 to get a larger `Noto Serif CJK SC Medium` size to close native looking.

Each edit will take a logout, login to be valid.

More information:

- https://learn.microsoft.com/en-us/globalization/input/font-technology
- https://shajisoft.com/shajisoft_wp/fontlink-for-cjk-on-english-windows-10 , a copy can be found in repository.

### MacType bug

Sometimes when using MacType, the change will not show, unless:

1. Turn off MacType(change load method to manually)
2. Reboot
3. Turn on MacType
4. Reboot again

### Principle (Steps)

Use FontForge, the opensource font edit software.

#### Fake Mono

Select 777 (0x309) U+0309 "hookabovecomb" COMBINING HOOK ABOVE,  
this shoule be a very rare to use char, Metrics -> Set Width to 599,  
which others is 600, so when saving it will not considered as monospace font.  
To a non-monospace font, Windows will not force a fallback font to be monospace.  
By doing this we get a font that 99% time monospace just one rare char width -1.

#### New font name

Edit font information\PS Names, rename to Noto Sans Fake Mono and add a new Unique ID,  
to allow it install with Noto Mono at the same time.

#### FontLink support

Edit font information\OS/2, use click - hold shift click, and ctrl click,  
select MS Code pages same as unmodified `Noto Mono`, or font link will not work.
