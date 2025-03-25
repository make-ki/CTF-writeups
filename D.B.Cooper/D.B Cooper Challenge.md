---
title: D.B Cooper Challenge

---
## Introduction

We embarked on the D.B Cooper Challenge, starting with the following resources:

- **GitHub Account**: [cooperghost230](https://github.com/cooperghost230)
- **Twitter Account**: [cooperghost230](https://x.com/cooperghost230)

## Initial Clues

On Twitter, we found two Base64 encoded messages:

```
Welcome to the hunt. Many have stepped onto this path, but only a few will make it to the end.
Every clue is a trap. Every step is a test. Keep your eyes sharp, your mind sharper.
You are not alone. Many teams are chasing the same answers, walking the same path.
The game has begun. Are you ready? #CooperGhost230
```

A QR code on the same Twitter account led us to a Google Drive link containing an audio file in Morse code. Decoding the Morse code revealed the message:

```
THIS IS NOT THE PATH TO HEAVEN MY CHILD YOU ARE GOING DIRECTLY TO HELL
```

## GitHub Investigation

Further investigation of the GitHub commits and logs led us to a Discord server: [https://discord.gg/jPCKcNpJ](https://discord.gg/jPCKcNpJ). We analyzed the server's profile picture and soundboard audios but found nothing significant.

## Location OSINT

A teammate, Kushal, managed to OSINT the location near the Bahrain F1 circuit. The brand in question was `lululemon`. Given Lewis Hamilton's recent move to Ferrari, we focused on the "Lewis" River near Skamania County, Washington, which hinted at Lewis Hamilton and the Bahrain F1 circuit.

We searched for parks near the Bahrain circuit and found the Al Areen Wildlife Park:

![Al Areen Wildlife Park](https://hackmd.io/_uploads/SyIi9UDiJe.png)

[Visit Al Areen Wildlife Park](https://earth.app.goo.gl/?apn=com.google.earth&isi=293622097&ius=googleearth&link=https%3a%2f%2fearth.google.com%2fweb%2fsearch%2fAl%2bAreen%2bWildlife%2bPark%2b%2526%2bReserve,%2bGulf%2bof%2bBahrain%2bRoad,%2bZallaq,%2bBahrain%2f%4026.00217769,50.50393576,10.21996924a,0d,90y,80.03971433h,69.13659518t,0r%2fdata%3dCrgBGokBEoIBCiUweDNlNDg0ZGYwMTExNTY4OWI6MHg5OGJlMzM5NDk2YTAxNjkxGe06ZX_qAzpAIZOpglFJP0lAKkdBbCBBcmVlbiBXaWxkbGlmZSBQYXJrICYgUmVzZXJ2ZSwgR3VsZiBvZiBCYWhyYWluIFJvYWQsIFphbGxhcSwgQmFocmFpbhgBIAEiJgokCfr4ceFZMTdAEWpJgM7_LzdAGUyViDdUI1JAIRmNTtwpI1JAQgIIASIwCixBRjFRaXBPeTlrdFZEdUlrOHYyU1R0UXdlYkQ2YktNZDdRcnNETHdUTFkxVBAFQgIIAEoNCP___________wEQAA)

## Zip File and Hidden Git

We found the exact location, and using the coordinates as a password, we opened a zip file containing `secret_message.mp4`. Standard video steganography techniques yielded no results. However, further investigation revealed a hidden `.git` file.

![Hidden Git](https://hackmd.io/_uploads/Hyc2s_Do1x.png)

The commit message was a ROT8000 encoded link to a rickroll, which we avoided clicking.

## Reverting Git

Using `git checkout`, we reverted the `.git` and found several files:

![Git Files](https://hackmd.io/_uploads/HkPzhdwjkx.png)

A file had this, ![image](https://hackmd.io/_uploads/BJg63Lvi1l.png)  N721AF <https://www.flightaware.com/live/flight/N721AF/history/20250215/1530ZZ/KGUC/KBVU> 
N721EF  <https://www.flightaware.com/resources/registration/N721EB>   ![image](https://hackmd.io/_uploads/Bya2a8voyl.png)   ![image](https://hackmd.io/_uploads/r1LATIvskx.png) 
Of course zoro....
## Arlong Park Brotli File

We extracted an Arlong Park brotli compressed file, which upon decompression, yielded a `.rar`, a `.jpeg`, and a `secret.txt`. The `secret.txt` contained a cipher at the bottom.

Using `steghide` we got `h3ll0w0rld`, we extracted further data:

![Steghide Extraction](https://hackmd.io/_uploads/BkNZ6_PsJe.png)

The `Alabasta.rar` extracted using `h3ll0w0rld` as pass, which revealed a PNG QR code:

![QR Code](https://hackmd.io/_uploads/SJzdIPPj1e.png)

The QR code gave the coordinates `123.456, 456.789`, marking the first poneglyph.

## Further Extraction

Using `wimextract`, we opened `skypiea.wim`:

![Skypiea WIM](https://hackmd.io/_uploads/BJt-A_Dskx.png)

The `Water7.tar.zst` file required no password:

![Water7 Tar](https://hackmd.io/_uploads/HkESRuPoJe.png)

Using `exiftool` on `Water7.jpeg`, we found the password `cutie_pie!` in the description:

![Exiftool Extraction](https://hackmd.io/_uploads/ryBj0dDo1e.png)

This revealed another poneglyph: `789.123, 321.654`.
Then another poneglyph down the lane: `106.168 172.253`

## Final Steps

We continued extracting files and found more poneglyphs:

```
123.456 456.789
789.123 321.654
789.123 321.654
106.168 172.253
```

Now for the [final island](https://youtu.be/KUav6PJz9TI?si=rDsiE_W9dR0nGQvf),
![me.psd](https://hackmd.io/_uploads/rJJDPYvoJg.png)

> makeki: "GABABABABA!!"
    "Joy Boy, huh...?!"
    "We were just too early!!"
![gang.psd](https://hackmd.io/_uploads/B1N1PtvsJl.png)
> "Ahahahaha!"
"What a funny story!!"

"They laughed... so hard... They laughed like crazy..."

Averaging these coordinates gave us `x: 451.9675, y: 318.0875`. Entering these into the provided executable yielded the password for the `YOU WON!!.pdf`.

## Conclusion

The challenge was both fun and challenging. Key learnings include the importance of validating approaches with challenge creators early on to avoid unnecessary rabbit holes. Despite some distractions, we successfully navigated through the clues to uncover the final solution.

![Final Image](https://hackmd.io/_uploads/BkUlAKwj1x.jpg)

**Final Coordinates**: `x: 451.9675, y: 318.0875`

**Password for `YOU WON!!.pdf`**: Derived from the executable using the averaged coordinates.
Could have skipped finding last poneglyph by seeing the decompiled binary :cat: 
![image](https://hackmd.io/_uploads/r1JGd9Fsyl.png)


---

