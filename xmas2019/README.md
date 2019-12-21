# X-MAS 2019 CTF

## Lapland Mission (50 points)

![Description](https://github.com/m3t4f0r4/CTF-writeups/blob/master/xmas2019/Lapland%20Mission/Description.png)

This is a Unity video game. When we open it, we see that a death screen appears within 0.5 seconds after a robot sees us and to get the flag we must kill all the robots.

![1](https://github.com/m3t4f0r4/CTF-writeups/blob/master/xmas2019/Lapland%20Mission/1.png)
![2](https://github.com/m3t4f0r4/CTF-writeups/blob/master/xmas2019/Lapland%20Mission/2.png)

The first thing we have to do is open the Assembly-CSharp.dll file with a .NET decompiler, in my case to patch it, I use [DnSpy](https://github.com/0xd4d/dnSpy).

We will navigate to PlayerControl and then to the method Die()

![DnSpy1](https://github.com/m3t4f0r4/CTF-writeups/blob/master/xmas2019/Lapland%20Mission/DnSpy1.png)

To patch it, we simply deactivate the death screen, adding "false" and instead of invoking the Respawn we invoke anything else, for example, HitRobot, so when the robots kill us, we will not reappear and we will kill the robots easily.

![DnSpy2](https://github.com/m3t4f0r4/CTF-writeups/blob/master/xmas2019/Lapland%20Mission/DnSpy2.png)
![Flag](https://github.com/m3t4f0r4/CTF-writeups/blob/master/xmas2019/Lapland%20Mission/flag.jpg)

## Noise (267 points)

![Description](https://github.com/m3t4f0r4/CTF-writeups/blob/master/xmas2019/Noise/Description.png)

When we heard the audio, we knew perfectly that it was an SSTV signal, so we used [RX-SSTV](http://users.belgacom.net/hamradio/rxsstv.htm) to decode it and generate an image.

![SSTV1](https://github.com/m3t4f0r4/CTF-writeups/blob/master/xmas2019/Noise/SSTV1.jpg)

## Best Friends (435 points)

![Description](https://github.com/m3t4f0r4/CTF-writeups/blob/master/xmas2019/Best%20Friends/Description.png)

When we look at the file strings, we see multiple encodings.

![Strings](https://github.com/m3t4f0r4/CTF-writeups/blob/master/xmas2019/Best%20Friends/strings.png)

To decode it, I used [CyberChef](https://gchq.github.io/CyberChef/) Base64> Base32> Hex.

![Cyberchef](https://github.com/m3t4f0r4/CTF-writeups/blob/master/xmas2019/Best%20Friends/cyberchef.png)

This gives us the next hint: ```Maybe B.F. stands for something other than best friend :)```
At first we thought it was something related to [Brainfuck Steganography](http://imrannazar.com/Steganography-with-Brainfuck), but no, after thinking for a long time we realized that it was the acronym for BruteForce, so we used [stegcracker](https://github.com/Paradoxis/StegCracker) (Steghide BruteForce) to decode the image.

![stegcracker](https://github.com/m3t4f0r4/CTF-writeups/blob/master/xmas2019/Best%20Friends/stegcracker.png)

Quickly give us an output with the password "celeste". 

![output](https://github.com/m3t4f0r4/CTF-writeups/blob/master/xmas2019/Best%20Friends/output.png)

it is a Base85 encoding, when we decode it, we will get the flag.

![flag](https://github.com/m3t4f0r4/CTF-writeups/blob/master/xmas2019/Best%20Friends/flag.png)


## Thank you Jiang Ying (409 points)

![Description](https://github.com/m3t4f0r4/CTF-writeups/blob/master/xmas2019/Thank%20you%20Jiang%20Ying/Description.png)

This challenge was quite easy, we just opened the file provided by the challenge with [IDA](https://www.hex-rays.com/products/ida/). If we see the main function graphically, we will quickly get the flag.

![flag](https://github.com/m3t4f0r4/CTF-writeups/blob/master/xmas2019/Thank%20you%20Jiang%20Ying/flag.png)
