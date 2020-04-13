# c0r0n4con CTF

## [In]SecureVault 1 (150 points)

Well, the challenge provides us a file with a .bin-runtime extension. After doing a quick Google search, I see that it's a Solidity Smart Contract.

To begin, we decompiled the bytecode, in my case I used JEB, although any online page like [ethervm.io](https://ethervm.io/decompile) or [trustlook](https://www.trustlook.com/services/smart.html) would be work.

We get the following code:
```
function sub_1C7(uint256* par1, uint256* par2) private pure returns (uint256) {
    uint256 var0;
    uint256* var1 = par1, var2 = par2;

    if(*par1 != *par2) {
        var0 = 0x0;
    }
    else {
        uint256* var3 = 0x0;

        while(!((unsigned char)(*var1 <= ((int256)var3)))) {
            uint256* var4 = var2, var5 = var3;

            if(!((unsigned char)(*var2 > ((int256)var3)))) {
                invalid();
            }

            var4 = (*(((uint256)(((int256)var4) + ((int256)var5))) + 0x20) / 0x100000000000000000000000000000000000000000000000000000000000000 * 0x100000000000000000000000000000000000000000000000000000000000000) & 0xff00000000000000000000000000000000000000000000000000000000000000;
            var5 = var1;
            uint256* var6 = var3;

            if(!((unsigned char)(*var1 > ((int256)var3)))) {
                invalid();
            }

            if(!((unsigned char)(((*(((uint256)(((int256)var5) + ((int256)var6))) + 0x20) / 0x100000000000000000000000000000000000000000000000000000000000000 * 0x100000000000000000000000000000000000000000000000000000000000000) & 0xff00000000000000000000000000000000000000000000000000000000000000) == ((int256)var4)))) {
                return 0x0;
            }
            else {
                var3 = (uint256*)(((char*)var3) + 0x1);
            }
        }

        var0 = 0x1;
    }

    return var0;
}


function sub_51() public view /*NON-PAYABLE*/ {
    var3 = msg.data.length;
    var4 = calldataload(0x4);
    var4 = var4 + 0x4;
    var5 = calldataload(var4);
    uint256 var7 = *0x40;
    *0x40 = (var5 + 0x1f) / 0x20 * 0x20 + var7 + 0x20;
    *var7 = var5;
    calldatacopy(var7 + 0x20, var4 + 0x20, var5);
    var5 = calldataload(0x24);
    var5 = var5 + 0x4;
    var6 = calldataload(var5);
    uint256 var8 = *0x40;
    *0x40 = (var6 + 0x1f) / 0x20 * 0x20 + var8 + 0x20;
    *var8 = var6;
    calldatacopy(var8 + 0x20, var5 + 0x20, var6);
    uint256 var0 = sub_1C7(var8, var7);
    uint256* var2 = *0x40;
    *var2 = (uint256)(var0 != 0x0);
    return(*0x40, var2 + 1 - *0x40);
}


function sub_317(uint256 par1, uint256 par2) private {
    uint256* var5;
    uint256 var3 = *0x40;
    *0x40 = var3 + 0x40;
    *var3 = 0x8;
    *(var3 + 0x20) = 0x6677686962626974000000000000000000000000000000000000000000000000;
    var3 = sub_1C7(par1, var3);

    if(var3 == 0x0) {
        var3 = *0x40;
        *var3 = 0x8c379a000000000000000000000000000000000000000000000000000000000;
        var3 += 0x4;
        var5 = var3 + 0x20;
        *var3 = (uint256)(((int256)var5) - var3);
        *var5 = 0x8;
        ++var5;
        *var5 = 0x4261642055736572000000000000000000000000000000000000000000000000;
        revert(*0x40, var5 + 1 - *0x40);
    }

    var3 = *0x40;
    *0x40 = var3 + 0x40;
    *var3 = 0x6;
    *(var3 + 0x20) = 0x7261626269740000000000000000000000000000000000000000000000000000;
    var3 = sub_1C7(par2, var3);

    if(var3 == 0x0) {
        var3 = *0x40;
        *var3 = 0x8c379a000000000000000000000000000000000000000000000000000000000;
        var3 += 0x4;
        var5 = var3 + 0x20;
        *var3 = (uint256)(((int256)var5) - var3);
        *var5 = 0xc;
        ++var5;
        *var5 = 0x4261642050617373776f72640000000000000000000000000000000000000000;
        revert(*0x40, var5 + 1 - *0x40);
    }

    var5 = *0x40;
    uint256* var7 = *par2;
    uint256 var8 = *par2;
    uint256* var9 = var5;
    uint256* var10 = par2 + 0x20;

    while(var8 >= 0x20) {
        *var9 = *var10;
        ++var9;
        ++var10;
        var8 -= 0x20;
    }

    uint256 var11 = 0x100 ** 0x20 - var8 - 0x1;
    *var9 = (~var11 & *var10) | (*var9 & var11);
    var3 = keccak256(*0x40, ((uint256)(((int256)var5) + ((int256)var7))) - *0x40);
    var5 = *0x40;
    var7 = var5 + 1;
    *var7 = var3;
    ++var7;
    *var5 = (uint256)(((int256)var7) - ((int256)var5));
    *var7 = 0x14;
    ++var7;
    *var7 = 0x596f75722070726976617465206b65792069733a000000000000000000000000;
    log1(*0x40, var7 + 1 - *0x40, 0x894707896d302733a35c9d7a681b0b21457fa3eb9560949ae3033e6346d8582d);
}


function sub_118() public /*NON-PAYABLE*/ {
    var3 = msg.data.length;
    var4 = calldataload(0x4);
    var4 = var4 + 0x4;
    var5 = calldataload(var4);
    uint256 var7 = *0x40;
    *0x40 = (var5 + 0x1f) / 0x20 * 0x20 + var7 + 0x20;
    *var7 = var5;
    calldatacopy(var7 + 0x20, var4 + 0x20, var5);
    var5 = calldataload(0x24);
    var5 = var5 + 0x4;
    var6 = calldataload(var5);
    uint256 var8 = *0x40;
    *0x40 = (var6 + 0x1f) / 0x20 * 0x20 + var8 + 0x20;
    *var8 = var6;
    calldatacopy(var8 + 0x20, var5 + 0x20, var6);
    sub_317(var8, var7);
    stop();
}
```

Well, we go to the interesting function that is sub_317, we see how "par1" is going to be our user
```
*(var3 + 0x20) = 0x6677686962626974000000000000000000000000000000000000000000000000;
    var3 = sub_1C7(par1, var3);
```
and "par2" is going to be the password.
```
*(var3 + 0x20) = 0x7261626269740000000000000000000000000000000000000000000000000000;
    var3 = sub_1C7(par2, var3);
```
Therefore we have the following:
```
User: fwhibbit
Password: rabbit
```
Finally we see that our private key has been hashed with an instruction called keccack256
```
keccak256(*0x40, ((uint256)(((int256)var5) + ((int256)var7))) - *0x40)
```
We see how it does a sum of var5 + var7 and subtracts a memory location * 0x40
```
var5 = *0x40;
uint256* var7 = *par2;
```
We would be left with the following:
```
keccak256((*0x40+*par2)-*0x40)
```
operation * 0x40 - * 0x40 is redundant so the instruction would finally look like this:
```
keccak256(*par2)
```
* par2 is the password so the flag is: flag{keccack256(rabbit)}

## DNACovid19 (100 points)


In this challenge I used the DNA binary sequence that we can find in [ctf-katana](https://github.com/JohnHammond/ctf-katana)

![DNA](https://github.com/m3t4f0r4/CTF-writeups/blob/master/c0r0n4con%20CTF/DNACovid19/coding.jpg)

I made a little script to decode the DNA Code
```
import string

alph = 'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ1234567890 .'

ciphertext = 'GAATAGTCGCTCGCGTAGTATTAAGAACTGTCGCTCGGAGCTTCGCTAGAAGGTGTACTCGGAGCTGATGTTGAAGAGTCGCTCGAAGCTCGTTATGAATAGTCCGTCGAGTAGTATTAAGAACTGTCCCTCGGAGCGTATGGGGAAGTTGTCCTCGGAGCGCGTGTGGAACTGTCGGAAGCAGCTCGTTACGAATATGTCCTCGAGTAGTATGTCGAACTGTCGGAAGCAGCTTCGCTG'

ciphertext = ciphertext.replace('A', '00')
ciphertext = ciphertext.replace('C', '01')
ciphertext = ciphertext.replace('G', '10')
ciphertext = ciphertext.replace('T', '11')

dc = ''
for i in range(0, len(ciphertext), 6):
    idx = int(ciphertext[i:i+6], 2)
    dc += alph[idx]

print dc
```

It returns a Base32 which we decode and we will get the flag

flag{MuRcIeLaG0_pAnGoL1n}

## Secure PWD artifact (300 points)
