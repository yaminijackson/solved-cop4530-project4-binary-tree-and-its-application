Download Link: https://assignmentchef.com/product/solved-cop4530-project4-binary-tree-and-its-application
<br>
Gain experience with a binary tree and its application in converting postfix expressions into infix expressions, as well as practice with developing recursive algorithms.

<strong>Task:</strong> Implement a binary expression tree and use the tree to convert postfix expressions into infix expressions

Project Requirements:

In this project, you are asked to develop a binary expression tree and use the tree to convert postfix expressions into infix expressions. In this project, a postfix expression may contain 4 types of operators: multiplication (*), division (/), plus (+), and minus (-). We assume that multiplication and division have the same precedence, plus and minus have the same precedence, and multiplication and division have higher precedence than plus and minus. All operators are left-associative (i.e. associate left-to-right).

<strong>Binary Expression Tree:</strong>. Build a binary expression tree class called “BET”. Your BET class must have a nested structure named “BinaryNode” to contain the node-related information (including, e.g., element and pointers to the children nodes). In addition, BET must at least support the following interface functions:

Public interface

<ul>

 <li><strong>BET()</strong>: default zero-parameter constructor. Builds an empty tree.</li>

 <li><strong>BET(const string&amp; postfix)</strong>: one-parameter constructor, where parameter “postfix” is string containing a postfix expression. The tree should be built based on the postfix expression. Tokens in the postfix expression are separated by spaces.</li>

 <li><strong>BET(const BET&amp;)</strong>: copy constructor — makes appropriate deep copy of the tree</li>

 <li><strong>~BET()</strong>: destructor — cleans up all dynamic space in the tree</li>

 <li><strong>bool buildFromPostfix(const string&amp; postfix)</strong>: parameter “postfix” is string containing a postfix expression. The tree should be built based on the postfix expression. Tokens in the postfix expression are separated by spaces. If the tree contains nodes before the function is called, you need to first delete the existing nodes. Return true if the new tree is built successfully. Return false if an error is encountered.</li>

 <li><strong>const BET &amp; operator= (const BET &amp;)</strong>: assignment operator — makes appropriate deep copy</li>

 <li><strong>void printInfixExpression()</strong>: Print out the infix expression. Should do this by making use of the private (recursive) version</li>

 <li><strong>void printPostfixExpression()</strong>: Print the postfix form of the expression. Use the private recursive function to help</li>

 <li><strong>size_t size()</strong>: Return the number of nodes in the tree (using the private recursive function)</li>

 <li><strong>size_t leaf_nodes()</strong>: Return the number of leaf nodes in the tree. (Use the private recursive function to help)</li>

 <li><strong>bool empty()</strong>: return true if the tree is empty. Return false otherwise.</li>

</ul>

Private helper functions (all the required private member functions must be implemented recursively):

<ul>

 <li><strong>void printInfixExpression(BinaryNode *n)</strong>: print to the standard output the corresponding infix expression. Note that you may need to add parentheses depending on the precedence of operators. You should not have unnecessary parentheses.</li>

 <li><strong>void makeEmpty(BinaryNode* &amp;t)</strong>: delete all nodes in the subtree pointed to by t.</li>

 <li><strong>BinaryNode * clone(BinaryNode *t)</strong>: clone all nodes in the subtree pointed to by t. Can be called by functions such as the assignment operator=.</li>

 <li><strong>void printPostfixExpression(BinaryNode *n):</strong> print to the standard output the corresponding postfix expression.</li>

 <li><strong>size_t size(BinaryNode *t)</strong>: return the number of nodes in the subtree pointed to by t.</li>

 <li><strong>size_t leaf_nodes(BinaryNode *t)</strong>: return the number of leaf nodes in the subtree pointed to by t.</li>

</ul>

Make sure to declare as const member functions any for which this is appropriate

<strong>Conversion to Infix Expression:</strong>. To convert a postfix expression into an infix expression using a binary expression tree involves two steps. First, build a binary expression tree from the postfix expression. Second, print the nodes of the binary expression tree using an inorder traversal of the tree.

The basic operation of building a binary expression tree from a postfix expression is similar to that of evaluating postfix expression. Refer to Section 4.2.2 for the basic process of building a binary expression tree from a postfix expression.

Note that during the conversion from postfix to infix expression, parentheses may need to be added to ensure that the infix expression has the same value (and the same evaluation order) as the corresponding postfix expression. Your result should not add unnecessary parentheses. Tokens in an infix expression should also be separated by a space. The following are a few examples of postfix expressions and the corresponding infix expressions.

<table width="100%">

 <tbody>

  <tr>

   <td width="50%">postfix expression</td>

   <td width="50%">infix expression</td>

  </tr>

  <tr>

   <td width="50%">4 50 6 + +</td>

   <td width="50%">4 + ( 50 + 6 )</td>

  </tr>

  <tr>

   <td width="50%">4 50 + 6 +</td>

   <td width="50%">4 + 50 + 6</td>

  </tr>

  <tr>

   <td width="50%">4 50 + 6 2 * +</td>

   <td width="50%">4 + 50 + 6 * 2</td>

  </tr>

  <tr>

   <td width="50%">4 50 6 + + 2 *</td>

   <td width="50%">( 4 + ( 50 + 6 ) ) * 2</td>

  </tr>

  <tr>

   <td width="50%">a b + c d e + * *</td>

   <td width="50%">( a + b ) * ( c * ( d + e ) )</td>

  </tr>

 </tbody>

</table>




<strong>Other Requirements</strong>:

<ul>

 <li>Analyze the worst-case time complexity of the private member function <strong>makeEmpty(BinaryNode* &amp; t)</strong> of the binary expression tree. Give the complexity in the form of Big-O. Your analysis can be informal; however, it must be clearly understandable by others. Name the file containing the complexity analysis as “analysis.txt”.</li>

 <li>You can use any C++/STL containers and algorithms</li>

 <li>If you need to use any containers, you must use the ones provided in C++/STL. Do not use the ones you developed in the previous projects.</li>

 <li>Create a makefile that will compile the provided driver program (see below) with your class, into an executable called “proj4.x”</li>

</ul>

<ul>

 <li>Your program MUST check invalid postfix expressions and report errors. We consider the following types of postfix expressions as invalid expressions: 1) an operator does not have the corresponding operands, 2) an operand does not have the corresponding operator. Note that an expression containing only a single operand is a valid expression (for example, “6”). In all other cases, an operand needs to have an operator.</li>

</ul>

Here is a driver program — <a href="https://www.cs.fsu.edu/~myers/cop4530/hw/hw4files/proj4_driver.cpp">proj4_driver.cpp</a> — to test the BET implementation. It accepts input from terminal, or the input is redirected from a file that contains the postfix expressions to be converted. Each line in the file (or typed by user) represents a postfix expression. We assume that the tokens in a postfix expression are separated by space. You can run out version of this driver program on linprog.cs.fsu.edu with this command:

~myers/dsprog/proj4.x

<strong>Note — ASSESSMENT for ABET requirements</strong>

This is our assignment that will satisfy the ABET assessment requirement that students in this course have achieved a degree of basic programming competence.