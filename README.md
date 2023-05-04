Download Link: https://assignmentchef.com/product/solved-cs635-advanced-oo-design-and-programming-assignment-2
<br>
<ol>

 <li>Use the Interpreter pattern to evaluate postfix expressions. The expression (1967 + 21) * sin(3) will be 1967 21 + 3 sin * in postfix. For more information about postfix see the <a href="https://en.wikipedia.org/wiki/Reverse_Polish_notation">Wikipedia</a> <a href="https://en.wikipedia.org/wiki/Reverse_Polish_notation">entry</a> You should support at least the operations +, -, *, / , lg (base 2) and sin. You may restrict the input to integer values. However the result may be a floating point number since we are including lg and sin. Postfix is used here to simplify the parsing. If you prefer to use normal arithmetic expressions you may.</li>

 <li>Implement a spreadsheet with 9 cells with a GUI. The cells are labeled $A, $B, $C, $D, $E,</li>

</ol>

$F, $G, $H, $I. (If you prefer you can use a 2-dimensional layout with the cells labeled $A$A, $A$B, $A$C, $B$A, $B$B, etc) A cell can contain either a formula, a number or be empty. A formula can contain numbers, reference to cells and the operations. In the first example below cell $A contains 1, $B contains the number 2, $C contains the formula $A $B +, and $E contains the formula $A $C +. We have an equation and a value view of the cells. The two tables below shows both the equation and the value views of the cells. Provide the user with a button to switch between views. That is you display the spreadsheet once and the user can toggle the view between the two views by clicking on a button. You need to provide a way for the user to enter values and equations. You either allow the user to enter the values directly in a cell or provide them with a separate input field to enter values and/or equations.

Value View

<table width="671">

 <tbody>

  <tr>

   <td width="27"> </td>

   <td width="47"><strong>$A</strong></td>

   <td width="27"> </td>

   <td width="47"><strong>$B</strong></td>

   <td width="28"> </td>

   <td width="47"><strong>$C</strong></td>

   <td width="61"><strong>$D</strong></td>

   <td width="13"> </td>

   <td width="75"><strong>$E</strong></td>

   <td width="28"> </td>

   <td width="46"><strong>$F</strong></td>

   <td width="75"><strong>$G</strong></td>

   <td width="75"><strong>$H</strong></td>

   <td width="75"><strong>$I</strong></td>

  </tr>

  <tr>

   <td width="27">2</td>

   <td width="47"> </td>

   <td width="27">3</td>

   <td width="47"> </td>

   <td width="28">5</td>

   <td width="47"> </td>

   <td width="61"> </td>

   <td width="13"> </td>

   <td width="75">8</td>

   <td width="28"> </td>

   <td width="46"> </td>

   <td width="75"> </td>

   <td width="75"> </td>

   <td width="75"> </td>

  </tr>

  <tr>

   <td width="27"> </td>

   <td width="47"> </td>

   <td width="27"> </td>

   <td colspan="2" width="75"> </td>

   <td width="47"> </td>

   <td width="61"> </td>

   <td colspan="3" width="116">Equation View</td>

   <td width="46"> </td>

   <td width="75"> </td>

   <td width="75"> </td>

   <td width="75"> </td>

  </tr>

  <tr>

   <td width="27"> </td>

   <td width="47"><strong>$A</strong></td>

   <td width="27"> </td>

   <td width="47"><strong>$B</strong></td>

   <td width="28"> </td>

   <td width="47"><strong>$C</strong></td>

   <td width="61"><strong>$D</strong></td>

   <td width="13"> </td>

   <td width="75"><strong>$E</strong></td>

   <td width="28"> </td>

   <td width="46"><strong>$F</strong></td>

   <td width="75"><strong>$G</strong></td>

   <td width="75"><strong>$H</strong></td>

   <td width="75"><strong>$I</strong></td>

  </tr>

  <tr>

   <td width="27">2</td>

   <td width="47"> </td>

   <td width="27">3</td>

   <td width="47"> </td>

   <td colspan="2" width="75">$A $B +</td>

   <td width="61"> </td>

   <td width="13"> </td>

   <td width="75">$B $C +</td>

   <td width="28"> </td>

   <td width="46"> </td>

   <td width="75"> </td>

   <td width="75"> </td>

   <td width="75"> </td>

  </tr>

 </tbody>

</table>

While in the value view if a user changes the value of a cell (for example cell $B) then all cells dependent on that cell need to be updated automatically. Note that more than one cell may require updating. <strong>One may be tempted to update all the cells whenever a user modifies one cell. However this will not scale to a really spreadsheet, so do not do it. When a user modifies one cell only update the cells that are effected by the change.</strong>

In this example above three cells depend on $A. If the user changes the value in cell $A all the values in the other cells need to be updated. Note that which cells depend on which cell is completely determined by the user. You have to be careful with circular dependancies. The following is just one example of a circular dependancy. This is an error condition which you have to detect.

<table width="671">

 <tbody>

  <tr>

   <td width="67"><strong>View</strong></td>

   <td width="67"><strong>$A</strong></td>

   <td width="67"><strong>$B</strong></td>

   <td width="67"><strong>$C</strong></td>

   <td width="67"><strong>$D</strong></td>

   <td width="67"><strong>$E</strong></td>

   <td width="67"><strong>$F</strong></td>

   <td width="67"><strong>$G</strong></td>

   <td width="67"><strong>$H</strong></td>

   <td width="67"><strong>$I</strong></td>

  </tr>

  <tr>

   <td width="67">Equa-tion</td>

   <td width="67">1</td>

   <td width="67">$A $C+</td>

   <td width="67">$D 1 +</td>

   <td width="67">$B 2 *</td>

   <td width="67"> </td>

   <td width="67"> </td>

   <td width="67"> </td>

   <td width="67"> </td>

   <td width="67"> </td>

  </tr>

  <tr>

   <td width="67">Value</td>

   <td width="67">1</td>

   <td width="67">Error</td>

   <td width="67">Error</td>

   <td width="67">Error</td>

   <td width="67"> </td>

   <td width="67"> </td>

   <td width="67"> </td>

   <td width="67"> </td>

   <td width="67"> </td>

  </tr>

 </tbody>

</table>

You might find the observer and state patterns useful here.

<ol start="3">

 <li>Add an undo mechanism to your spreadsheet. The undo mechanism should be unlimited. However the undo history does not have to span multiple invocations of the program. That is when you start the program your undo history can start empty. Each change the user makes in either a value or an equations is to be undoable.</li>

</ol>


