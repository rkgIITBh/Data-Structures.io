## Huffman Encoding Algorithm  

Huffman encoding uses a greedy approach. Initially, it starts with a forest
of trees. Each symbol is associated with a node of a tree in the forest.
The trees in the forest are merged in a greedy approach. A new joint symbol replaces a pair of
least frequently occurring symbols. The sum of frequencies of the old pair of symbols becomes the frequency of the new symbol. The merging, as explained, reduces the symbol set reduces by one. Therefore, each 
successive merging of trees in the forest reduces the complexity of the problem by 1. Finally, one tree gets built. The figure below illustrates the successive iterations for merging operations. 
<p align="center">
<img src="../images/huffmanEx1a.jpg"> 
</p>
The method assigns the shortest code to the most frequently occurring 
symbol and the longest code to the least frequent symbol in the 
input. A binary tree is constructed bottom-up for the codewords where each leaf node represents a symbol or a character in the input. A left
branch (pointing to the left child) from a node is labeled a 0 and a
right branch (pointing to the right child) is labeled a 1. Now the string
of labels starting from 
the root of the Huffman tree gives the codeword for a symbol.
The final Huffman tree is obtained by merging the 2nd and the 4th tree. 
<p align="center">
<img src="../images/huffmanEx2.jpg"> 
</p>
The codewords for the symbols are shown in the table alongside. 

The optimality of the Huffman encoding scheme can be evaluated by computing the number 
of bits used for an input text. Let <i>c</i> and <i>f(c)</i> respectively
denote a character and its frequency in the input. Then the number of bits <i>B(T)</i> required for the input 
is given by the following expression:
<p align="center">
<img src="https://latex.codecogs.com/svg.image?B(T)=\sum_{c\in&space;A}f(c).depth(c)" title="B(T)=\sum_{c\in A}f(c).depth(c)" />
</p>
where <i>T</i> is the Huffman tree for the alphabet set <i>A</i>.

Starting with a forest of tree consisting of single nodes representing each character, in each iteration a pair of trees with two least frequencies are 
merged. To prove correctness we use the following recursive formulation  
<ul>
<li>Let initial set of symbols be <i>A</i> in which <i>a</i> and <i>b</i> are two symbols of least frequencies.</li>
<li>Let <i>A<sup>'</sup></i> =<img src="https://latex.codecogs.com/svg.image?(A&space;-&space;\{a,b\})\cup&space;\{c\}" title="(A - \{a,b\})\cup \{c\}" />  where <i>c</i> is the new symbol that replaces both <i>a</i> and <i>b</i> </li>
<li>Recursively use the Huffman algorithm to computer prefix code for <i>A<sup>'</sup></i>. </li> 
<li>After getting optimal code for <i>A<sup>'</sup></i> put back <i>a</i> 
and <i>b</i> as the children of <i>c</i> in the Huffman tree of 
<i>A<sup>'</sup></i></li> 
</ul>

The critical part of the proof is to show that there exists an optimal prefix
code where <i>a</i> and <i>b</i> are siblings.

Let us now analayze the Huffman encoding algorithm. We maintain a heap of symbols alongwith their associated frequencies. So, two deleteMin operations on the
heap gives us the pair of least frequent symbols in the text. After deleting the least frequently occurring symbol pair we insert a new symbol with frequency
equal to sum of the frequencies of the deleted symbols. It effectively implements the merge operation. Every time one symbol is reduced from the current set of
symbols. So, <img src="https://latex.codecogs.com/svg.image?|A|-1" title="|A|-1" /> iterations are required. Building heap requires <img src="https://latex.codecogs.com/svg.image?\log&space;|A|" title="\log |A|" /> time. Heap operations require <img src="https://latex.codecogs.com/svg.image?O(|A|\log&space;|A|)" title="O(|A|\log |A|)" /> time. 

 We will continue the proof in the next blog. Click the [link here](../CODES/HuffmanCode/index.md) for the source code implementing the Huffman encoding scheme. 

[Back to Index](../index.md)