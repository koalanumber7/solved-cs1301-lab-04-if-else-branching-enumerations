Download Link: https://assignmentchef.com/product/solved-cs1301-lab-04-if-else-branching-enumerations
<br>
This lab builds upon lab 3, using <strong>if-else</strong> and other branching statements to classify short messages (like tweets) based on keywords in the message. This is a task that might reasonably be done in real-world situations.  E.g., certain tweets might contain information (e.g., a request for help, a fire sighted) that must be acted on quickly, and computer programs could be used to identify these based upon the text in the message.

In this lab, you will create a Java enumeration called <strong>MessageCategory</strong> inside of <strong>ClassifyMessage</strong> that lists several message categories (<strong>NEED, OFFER, ALERT, INFO, UNKNOWN</strong>). Your program will parse the text of a user specified message, identify the category of the message, and assign this value to a variable (<strong>category</strong>) declared to be of type <strong>MessageCategory </strong>(only values from the enumeration can be assigned to the variable)<strong>.</strong> You will also identify the latitude and longitude specified in the message and determine whether these are within ranges defined elsewhere in the program.

Exercise – Using Enumerations and If-Else statements

Since the primary purpose of this lab is not String manipulation, we will use a simpler message format than that found in lab 3. You will still use the <strong>Scanner</strong> and <strong>String</strong> classes, however.

You may assume that the messages processed by the program all have the following format:

<em>category</em> <em>latitude</em> <em>longitude</em> <em>payload</em>

where <em>category</em> is a single keyword indicating the message category (its type in Lab 3), <em>latitude</em> and <em>longitude</em> are both floating point numbers, and <em>payload</em> is a string of text (potentially containing arbitrary characters) constituting the primary body of the message.  For instance, the message




offer 40.022 -105.226 free essential supplies 4 evacs pets, 2323 55th st, boulder

conforms to the above format. Additional sample messages are provided at the end of this document.  You should use them to test your code.

<h2>Instructions</h2>

<ol>

 <li>Create a new class called <strong>ClassifyMessage </strong>(stored in a file called <strong>java</strong>).</li>

 <li>Declare the enumeration <strong>MessageCategory</strong> by adding the following line:</li>

</ol>

<strong>enum MessageCategory</strong> <strong>{NEED, OFFER, ALERT, INFO, UNKNOWN}</strong>

<ul>

 <li>Where does this line of code belong? In the main method?  In <strong>ClassifyMessage</strong>?  Think about this</li>

 <li>You should declare the following variables in your program:</li>

</ul>

<table width="0">

 <tbody>

  <tr>

   <td width="24">o</td>

   <td width="144"><strong>catString</strong>:</td>

   <td width="96"><strong>String </strong></td>

   <td width="263"><strong>// </strong>The raw text of the message’s category</td>

  </tr>

  <tr>

   <td width="24">o</td>

   <td width="144"><strong>payload</strong>:</td>

   <td width="96"><strong>String </strong></td>

   <td width="263"><strong>// </strong>The primary content of the message</td>

  </tr>

 </tbody>

</table>

o <strong>latitude</strong>:                    <strong>double     // </strong>The latitude indicated in the message o <strong>longitude:</strong>       <strong>double     // </strong>The longitude indicated in the message o <strong>isInRange:     boolean // </strong>A “flag” indicating whether the latitude and

<strong>                         // </strong>longitude values are within bounds o <strong>category:    </strong><strong>MessageCategory</strong><strong> // </strong>The message’s category

<ol start="3">

 <li>Additionally, you should declare the following <strong>double</strong> variables and initialize them to the shown values. These define geographic boundaries that the program uses. Some messages will originate from within those bounds, other messages will not. <strong>Is it a good idea to make these constants? </strong>

  <ul>

   <li><strong>south</strong>            <strong>double     </strong>882343                   <em>// southernmost latitude</em> o <strong>north</strong>     <strong>double     </strong>40.231315                   <em>// northernmost latitude</em> o <strong>west</strong>          <strong>double     </strong>-105.743511                   <em>// westernmost longitude</em> o <strong>east</strong>         <strong>double</strong>           -104.907864       <em>// easternmost longitude</em></li>

  </ul></li>

 <li>After the variables have been declared, write a statement to prompt the user with the following message:</li>

</ol>

<strong>Please enter a formatted message: </strong>

<ol start="5">

 <li>Use the <strong>keyboard</strong> object’s <strong>next()</strong>, <strong>nextDouble(),</strong> and <strong>nextLine()</strong> methods to read in values for <strong>catString</strong>, <strong>latitude</strong>, <strong>longitude</strong>, and <strong>payload</strong>. You may assume that the message is entered as a single line of text and formatted as described earlier.</li>

 <li>For <strong>payload</strong> (and <strong>catString</strong>, if needed) you should trim (using the <strong>trim()</strong> method of the <strong>String</strong> class, if needed) any leading and trailing white spaces from the text.</li>

 <li>Use a multi-branch if-else statement to match the value stored in <strong>catString</strong> to one of the elements of the enumeration <strong>MessageCategory</strong>.  The conditions should be the following:

  <ul>

   <li>If the value of <strong>catString</strong> is one of <strong>“fire”</strong> or <strong>“smoke”,</strong> then <strong>category</strong> should be assigned the value <strong>ALERT</strong>.</li>

   <li>Otherwise, if the value of <strong>catString</strong> is <strong>“need”</strong>, then <strong>category</strong> should be assigned the value <strong>NEED</strong>. o Otherwise, if the value of <strong>catString</strong> is <strong>“offer”</strong>, then <strong>category</strong> should be assigned the value <strong>MessageCategory.OFFER</strong>.</li>

   <li>Otherwise, if the value of <strong>catString</strong> is one of <strong>“structure”,</strong> <strong>“road”,</strong> <strong>“photo”,</strong> or <strong>“evac”,</strong> then <strong>category</strong> should be assigned the value <strong>INFO</strong>. o Otherwise, <strong>category</strong> should be assigned the value <strong>MessageCategory.UNKNOWN</strong>.</li>

  </ul></li>

</ol>

When comparing the strings, you should use the <strong>equalsIgnoreCase</strong> method.  Why use the <strong>equalsIgnoreCase</strong> method?  Why not use <strong>==?</strong>

<ol start="8">

 <li>Use another if-else statement to determine whether the latitude and longitude specified in the message are within the geographic boundaries indicated by <strong>north</strong>, <strong>south</strong>, <strong>east</strong>, and <strong>west</strong>. Variable <strong>isInRange</strong> should be assigned the value <strong>true</strong> if and only if <strong><em>both</em></strong> of the below conditions are met.</li>

</ol>

Otherwise, <strong>isInRange</strong> should be assigned the value <strong>false</strong>.

<ol>

 <li>If <strong>latitude ≥ south</strong> and <strong>latitude ≤ north</strong>.</li>

 <li>If <strong>longitude ≥ west</strong> and <strong>longitude ≤ east</strong>.</li>

</ol>

<h1>Additional Requirements</h1>

These are things that make the graders lives easier, and ultimately, you will see in the real world as well. Remember the teaching staff does not want to touch your code after they gave you requirements; they want to see the perfect results they asked for! Here is a checklist of things you can<strong> lose points</strong> for:




<ul>

 <li>(10 points) If the source file(s)/class(es) are named incorrectly (case matters!)</li>

 <li>(10 points) If your source file(s) have a package declaration at the top</li>

 <li>(10 points) If any source file you submit is missing your Statement of Academic Honesty at the top of the source file. All submitted source code files must contain your Statement of Academic Honesty at the top of each file.</li>

 <li>(10 points) If you have more than one instance of Scanner in your program. Your program should only have one instance of Scanner.</li>

 <li>(15 points) Inconsistent I/O (input/output) that does not match our instructions or examples exactly (unless otherwise stated in an assignment’s instructions). Your program’s I/O (order, wording, formatting, etc.) must match our examples and instructions.</li>

 <li>(100 points) If the source file(s) are not submitted before the specified deadline’s late period ends (48 hours after the deadline) or if they do not compile.</li>

 <li>(25 points) Late penalties will be deducted as per the course syllabus.</li>

 <li>If your (10 points) comments or (10 points) variables are “lacking” o Here, “lacking” means that you or a TA can find <strong>any</strong> lines of code or variables that take more than 10 seconds to understand, and there is no comment, or the variable name does not make sense (variable names like <strong>b</strong>, <strong>bb</strong>, <strong>bbb</strong>, etc. <strong>will</strong> <strong>almost never be acceptable) </strong></li>

 <li>(10 points) Indentation is not consistent throughout your source code o Refresh your memory of indentation patterns in chapter 2 in the course textbook o Be careful of a combination of tabs and spaces in your files (use one or the other)!</li>

</ul>




If any of the above do not make sense to you, talk to a TA, or ask on Piazza!