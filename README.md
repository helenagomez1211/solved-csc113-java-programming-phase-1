Download Link: https://assignmentchef.com/product/solved-csc113-java-programming-phase-1
<br>



You are designing and implementing a simple java application to help your teachers in preparing course exams. More than one teacher can use it, by entering course name only. All questions in this application persist beyond the execution of each session, which means after each session you should save questions in object file.

The following UML describes the required classes in general (<strong>check the pdf file</strong>):




<ol>

 <li><strong>Class Diagram:</strong></li>

</ol>

<img decoding="async" data-recalc-dims="1" data-src="https://i0.wp.com/www.ankitcodinghub.com/wp-content/uploads/2020/02/490.png?w=980&amp;ssl=1" class="aligncenter lazyload" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==">

 <noscript>

  <img decoding="async" class="aligncenter" src="https://i0.wp.com/www.ankitcodinghub.com/wp-content/uploads/2020/02/490.png?w=980&amp;ssl=1" data-recalc-dims="1">

 </noscript>

<ol start="2">

 <li><strong>Class Description:</strong></li>

</ol>

Implement the above UML using the following description  <strong>Class Question</strong><strong>            </strong>

<ul>

 <li>String text: question text</li>

 <li>String qID: question identifier, unique for each question start with chapter number followed by ”_” followed by question number. For example (ch08_1), means question 1from chapter 8.</li>

 <li>double pGrade: possible grade</li>

 <li>Question (String text, String qID, double pGrade): constructor to initialize question’s attributes</li>

 <li>Question (Question q): copy constructor</li>

 <li>String formattedQ():<strong>an abstract</strong> method that return a formatted string of question depends on the type of question</li>

 <li>String formattedQwithA():<strong>an abstract</strong> method that return a formatted string of question along with correct answer depends on the type of question.</li>

 <li>Setters and Getters as needed</li>

</ul>

<h1>Class MCQ</h1>

<ul>

 <li>int correctAnswer; index of correct answer</li>

 <li>String [] choices: List of 4 string represents choices for this question</li>

 <li>String formattedQ():method that return a formatted string of MCQ question using the following format</li>

</ul>

Choose                                                                                 the         correct  answer: Choose the         correct  answer:

qID:text                                                                                                         ch04_1:Which          of            the         following             is                                                                                                                                   true    about    inheritance         in            Java?

1:choices[0]                                                                                 1:We            cannot  override               private  methods

2:                                                                                                   choices[1]     2:We     cannot  override               protected                                                                                                        methods

3:                                                                                                choices[2]       3:We     cannot  override               private  methods

4:                                                                 choices[3]       4:None




<ul>

 <li>String formattedQwithA(): return a formatted string of question along with correct answer. Use formattedQ() and “Correct Answer is ” correctAnswer</li>

</ul>

<h1>Class FillBlankQ</h1>

<ul>

 <li>String correctAnswer: contain answer</li>

 <li>String formattedQ():method that return a formatted string of Fill Blank question using the following format.</li>

 <li>String formattedQwithA():return a formatted string of question along with correct answer Use formattedQ() and “Correct Answer is ” correctAnswer</li>

</ul>

<h1>Class TrueFalseQ</h1>

<ul>

 <li>boolean correctAnswer: answer for question</li>

 <li>String formattedQ():method that return a formatted string of True or False question using the following format</li>

 <li>String formattedQwithA():return a formatted string of question along with correct answer. Use formattedQ() and “Correct Answer is ” correctAnswe</li>

</ul>

<h1>Class QuestionBank</h1>

<ul>

 <li>int noQ: number of questions in qList</li>

 <li>String courseName: name of the course</li>

 <li>Question [] qList: array of question</li>

 <li>QuestionBank( String cname ): constructor to initialize attribute</li>

 <li>boolean addQuestion(Question q): this methods adds the received question object in the first empty position in qList. If and only if the question q is not <strong>found</strong> in qList and return true. False otherwise.</li>

 <li>void removeAllQuestion (String ids []): this methods remove <strong>all questions</strong> with qID equals to IDs in the received array Use replacement with shifting.</li>

 <li>int findQuestion (Question q): searches the qList array for the question q, returns its location if found, or -1 otherwise.

  <ul>

   <li>Note<u>: to avoid redundant questions</u>, two questions considered equals if they have same qID or same text</li>

  </ul></li>

</ul>




<ul>

 <li>int countChapterQuestions (String  cName): this methods return number of questions in qList belongs to received chapter name  cName  o Note: chapter name is included in the question ID

  <ul>

   <li>Hint: to avoid logical error when comparing two String, compare both String after converting them to lower case</li>

  </ul></li>

 <li>int loadQuestions(String fname) :This method read questions objects (object by object) from the object file <strong>fname </strong>and then adds them into the <strong>qList </strong> The method ends when no more object left for reading. Then returns the number of objects successfully added to the <strong>qList </strong>array.

  <ul>

   <li>Note: file name should be same as course name, otherwise an appropriate exception – Illegal Argument Exception -should be generated.</li>

  </ul></li>

 <li>void saveQuestions() :This method write to an object file called (courseName.ser) all the questions in the <strong>qList</strong> array (object by object).</li>

 <li>Question [] getRandomQuestions( int n): This method return an array of <strong>n </strong>different questions randomly selected from <strong>qList</strong>. If the total number of questions in <strong>qList</strong> is less than n, an <u>IllegalArgumentException</u> should be generated.</li>

 <li>Question [] getChapterQuestions( int n,String cName): This method return the first  n questions</li>

</ul>

from <strong>qList</strong> that belongs to the received chapter name cName. If number of questions for this chapter is less than n it should return an array containing the available questions only.

<ul>

 <li>Note: The size of returned array is equal to the number of questions from specified chapter</li>

 <li>Hint: to avoid logical error when comparing two String, compare both String after converting them to lower case</li>

</ul>

<h1>Class ExamManager</h1>

<ul>

 <li>QuestionBank qBank: question bank for specific course</li>

 <li>ExamManager (String courseName): constructor to initialize attribute and <strong>fill</strong> question bank <strong>qBank</strong> with question objects from file (courseName.ser) <u>if file exists</u>. If file not found the appropriate message should be printed.</li>

 <li>boolean addNewQuestion (Question q): this method adds the received question q object to <strong>qBank</strong></li>

 <li>void removeChapterQuestions(String chapterName): this method removes all questions belong to the received chapter name chapterName o Hint: you should use removeAllQuestion (String ids[])</li>

</ul>



















<ul>

 <li>double generateExam (String header, int n, String chapterName, boolean withAnswers ): This method should write into a text file called (coursenameExam.txt). The received header (which contains the exam information) should appear at the beginning of the text file. If the received <strong>chapterName</strong> is an empty string, then <strong>n</strong> questions are randomly selected from qBank and should be written to this text f-<u>i</u>le, otherwise n questions from the specified chapter</li>

</ul>

<span style="text-decoration: line-through;">I </span><strong>chapterName</strong> should be written. If the <strong>withAnswers</strong> is true then the generated file should

contain correct answer for each question. This method should return the total number of possible grades for this exam.

<ul>

 <li>void exportQBank() this method should save all questions in qBank to be used in the next session o Hint: Use saveQuestions()</li>

</ul>

<h1>Class TestApp</h1>

<ul>

 <li>main (String args []) o Given to you to test your implementation</li>

</ul>




<ol start="3">

 <li><strong>Deliverable and rules</strong></li>

</ol>

You must deliver:

<ul>

 <li>Source code submission to LMS. You have to upload all classes in a zipped file. (section#_group#_CSC113Project)</li>

 <li>The submission deadline is <strong>9 March 2019.</strong></li>

</ul>

You have to read and follow the following rules:

<ul>

 <li><strong>The specification given in the assignment (class and interface names, and method signatures) must not be modified. Any change to the specification results in compilation errors and consequently the mark zero.</strong><strong> <u>(Use the same name in UML)</u></strong><strong>        </strong>o <strong>For testing purpose, you should <u>add the setters/getters methods</u> even if you didn’t use them.  </strong><strong>     </strong></li>

 <li>This assignment is a group assignment. Each group contains <strong>3-4 students only </strong>from the same section.</li>

 <li>The submitted code will be evaluated automatically using Junit Tests and discussion during week 10 Lab time.</li>

 <li><strong>All submitted code will be automatically checked for similarity, and if plagiarism is confirmed penalties will apply, (-2) in the total marks of the project.</strong></li>

</ul>