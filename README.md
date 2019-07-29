# VHDL_SHA2-256
- Single chunk core: a not so general VHDL SHA-2 core with 256 bits hash. Medium footprint. Digests only a single chunk of data ie. 512 bits, meaning the algorithm's feedback of loading the input of the digestion with the output of the previous chunk is not implemented. The reason behind this is that I developed it for password hashing, considering a 16 byte nonce and a 40 byte password being enough.
- Pipe element core: it is the pipelined description of the digestion function and the non linear shift register which both are capable of having 3 pipe stages. The pictures added - original taken from Wikipedia - show how the placement of D-flip-flops is being derived. Adding 64 stages of this core consecutively results in a 192 layer open pipeline digesting 512 bit chunks with no data feedback.
- In the future the pipelined design's compression function needs to be able to be initialized with custom values so that they can finish the calculation a Bitcoin block, of which only the last 512 bits are changing rapidly. (Meaning a kind of calculation like a length extension attack against a plain SHA2-256.)
- To be noted pipelined SHA2 can not digest a single data thread as many times faster as many stages it has, but is capable of digesting as many data threads parallely.
