---
title: "The Engima Machine"
excerpt_separator: "<!--more-->"
---

### [Engima Machine](https://github.com/KaiSkiFox/EngimaMachine)

Engima Machine was famous in World War II, as its revolutionary complex to decrypt yet simple to encode/decode. If you have the settings for one machine, the message is encoded and can be decoded by similar machines with the exact setting. However, bystanders without any knowledge, will have to try over 415,182,802,944 potential permutations to stumble onto the correct one.  

My idea is to remake the Engima machine, not in real life, but in computers. To achieve this I decided to use C#, not only a simple language, but it will also allow me to expand this project with more visualization in unity. Then I separate the sections of the Engima machine into three different parts: the Rotors, the Reflectors, and the Plugboards.  I also decided to add additional features, adding the ability to export the rotor table and use a randomized rotor wiring setting and reflector wiring to greatly increase customizability.  

After vigorously watching documentary videos explaining the inner working of the Engima machine, and reading the guide from Engima Wirings, I thought I was ready. But in truth, I was far from it. One of the major issues took place in reflector design. At first I assumed a reflector would behave similarly to that of a rotor. Input signal `A` would direct to `B` just like a rotor. However, the oversight of mine is the decoding process. Because if the Reflector behaves similarly to a Rotor, during the decode process signal `B` would not direct the signal back to `A`, instead it would direct it to another wiring path. The fix was rather simple, ensuring that the bath of `A` to `B` while `B` must also return to `A`.  

To allow a faster process, I use integers instead of letters during rotor signal transition. 0=`A`, 1=`B`, etc. This is dubbed as both the letter index and also position index for the next rotor table. So each rotor table would contain a map that direct the current input into the next input for the proceeding rotor. To simulate a rotor moving, I designed the rotor to contain a `rotateSequence`, instead of checking the letter, each time a rotor is moved, the notch would also shift, so the integer `rotateSequence` reaches 0, the current rotor sends a signal to the next rotor and the next rotor move. One important mechanism for the rotor set is the double stepping of the middle rotor which is an intricirate design but easily overlooked.  

On theory, the rotor notch would be only allowed the next rotor to be moved, but in real life, the rotor notch would allowed the movement for both the rotor with notch and the following rotor. Which means when middle rotor reached a `rotateSequence` of 0, the rotor must send a signal to next rotor and allowed the rotation of the middle rotor.  

The finished product was then tested with exisiting engima code, from multiple source. Ensuring the preset rotor wiring will behaive the same like  other Enigma Mahcine, so the message from those machine can also be decoded without error.  
