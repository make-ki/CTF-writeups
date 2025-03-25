### Description:
Amo, who loved Caesar ciphers, ended up creating a more powerful Byte-Caesar cipher!


### Attempt:

On opening the python script, you could see that both the encrypt and decrypt methods were created already for Caesar class. Encoded text provided in output file was to just be decoded using the same script. The key was a rand from range of 1 to 255 so we could brute force all the keys and grep for `DH{` which was the flag format given. 
Now all we had to do was use `bytes.fromhex(hex_string)` and the provided `decrypt` method. 
I wasted some time here trying to figure out what data type was to be put inside what.


### Learnings:
1) b'' means byte literal and f'' means string literal
2) You could always check data types by `print(type(foo))`

