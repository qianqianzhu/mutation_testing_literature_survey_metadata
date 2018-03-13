# Generalised classification of mutation operators
As researchers in mutation testing, we found that different mutation testing tools use different naming conventions for their mutation operators. For example, in MuJava[[1]](#ref1), the mutation operator which replaces relational operators with other relational operators is called "Relational Operator Replacement", while that is named "Conditionals Boundary Mutator" in PIT[[2]](#ref1). Therefore, we saw a need to compose a generalised classification of mutation operators, which enables us to more easily compare mutation operators from different tools or definitions.

The method we adopted here to generate the generalised classification is to group the similar mutation operators among all the existing mutation operators in the literature based on how they mutate the programs. Firstly, mutation testing can be applied to both program source code and program specification. Thus, we classified the mutation operators into two top-level groups: program mutation and specification mutation operators, in similar vein to Jia and Harman's survey.
As we are more interested in program mutation, we further analysed this area and summarised different mutation operators based on literature. More specifically, we first followed the categories and naming conventions of MuJava[[3]](#ref3)[[4]](#ref4) and Proteum[[5]](#ref5) as their mutation operator groups are more complete than the others. Based on the mutation operator groups from MuJava and Proteum, we further divided the program mutation operators into three sub-categories: expression-level, statement-level and others. The expression-level mutation operators focus on the inner components of the statements, i.e., operators (method-level mutation operators in MuJava[[3]](#ref3) and operands (Constant and Variable Mutations in Proteum[[5]](#ref5), while the statement-level ones mutate at least a single statement (Statement Mutations in Proteum[[5]](#ref5). As we are interested in a more generalised classification independent of the programming language, we came up with the class of "others" to include mutation operators related to the programming language's unique features, e.g. Objected-Oriented specific and Java-specific mutation operators (Class Mutation in MuJava[[4]](#ref4). It is important to note that our generic classification of mutation operators aims to provide an overall distribution of different mutation operator groups. Thus we did not look into lower-level categories.

Our generic classification of mutation operators is as follows:

  1. Specification mutation
  2. Program mutation
    - (a) Expression-level
        - (i) **arithmetic operator**:
        it mutates the arithmetic operators (including addition "+", subtraction "-", multiplication "\*", division "/", modulus "%" , unary operators "+", "-", and short-cut operators "++", "--")<sup>[1](#myfootnote1)</sup> by replacement, insertion or deletion.
        - (ii) **relational operator:**
        it mutates the relational operators (including ">", ">=", "<", "<=", "==", "!=") by replacement.
        - (iii) **conditional operator:**
        it mutates the conditional operators (including and "&",  or "|", exclusive or "^", short-circuit operator "&&", "||", and negation "!") by replacement, insertion or deletion.
        - (iv) **shift operator:**
        it mutates the shift operators (including ">>", "<<" and ">>>") by replacement.
        - (v) **bitwise operator:**
        it mutates the bitwise operators (including bitwise and "&", bitwise or "|", bitwise exclusive or "^" and bitwise negation "~") by replacement, insertion or deletion.
        - (vi) **assignment operator:**
        it mutates the assignment operators (including the plain operator "=" and short-cut operators "+=", "-=", "\*=", "/=", "%=", "&=", "|=", "^=", "<<=", ">>=", ">>>=") by replacement. Besides, the plain operator "=" is also changed to "==" in some cases.
        - (vii) **absolute value:**
        it mutates the arithmetic expression by preceding unary operators including _ABS_ (computing the absolute value), _NEGABS_ (compute the negative of the absolute value) and _ZPUSH_ (testing whether the expression is zero. If the expression is zero, then the mutant is killed; otherwise execution continues and the value of the expression is unchanged)<sup>[2](#myfootnote2)</sup> system. In some cases, this operator only applies the absolute value replacement.}.
        - (viii) **constant:**
        it changes the literal value including increasing/decreasing the numeric values, replacing the numeric values by zero or swapping the boolean literal (_true_/_false_).
        - (ix) **variable:**
        it substitutes a variable with another already declared variable of the same type and/or of the compatible type.<sup>[3](#myfootnote3)</sup>
        - (x) **type:**
        it replaces a type with the other compatible types including type casting.<sup>[4](#myfootnote4)</sup>
        - (xi) **conditional expression:**
        it replaces the conditional expression by _true_/_false_ so that the statements following the conditional always execute or skip.
        - (xii) **parenthesis:**
        it changes the precedence of the operation by deleting, adding or removing the parentheses.
    - (b) Statement-level
      - (i) **_return_ statement:**
      it mutates _return_ statement in the method calls including _return_ value replacement or _return_ statement swapping.
      - (ii) **_switch_ statement:**
      it mutates _switch_ statements by making different combinations of the _switch_ labels (_case_/_default_) or the corresponding block statement.
      - (iii) **_if_ statement:**
      it mutates _if_ statements including removing additional semicolons after conditional expressions, adding an _else_ branch or replacing last _else if_ symbol to _else_.
      - (iv) **statement deletion:**
      it deletes statements including removing the method calls or removing each statement<sup>[5](#myfootnote5)</sup>.
      - (v) **statement swap:**
      it swaps the sequences of statements including rotating the order of the expressions under the use of the _comma_ operator, swapping the contained statements in _if-then-else_ statements and swapping two statements in the same scope.
      - (vi) **brace:**
      it moves the closing brace up or down by one statement.
      - (vii) **_goto_ label:**
      it changes the destination of the _goto_ label.
      - (viii) **loop trap:**
      it introduces a guard (trap after n<sup>th</sup> loop iteration) in front of the loop body. The mutant is killed if the guard is evaluated the n<sup>th</sup> time through the loop.
      - (ix) **bomb statement:**
      it replaces each statement by a special _Bomb()_ function. The mutant is killed if the _Bomb()_ function is executed which ensures each statement is reached.
      - (x) **control-flow disruption (break/continue):**
      it disrupts the normal control flow by adding, removing, moving or replacing _continue_/_break_ labels.
      - (xi) **exception handler:**
      it mutates the exception handlers including changing the _throws_, _catch_ or _finally_ clauses.
      - (xii) **method call:**
      it changes the number or position of the parameters/arguments in a method call, or replace a method name with other method names that have the same or compatible parameters and result type.
      - (xiii) **_do_ statement:**
      it replaces _do_ statements with _while_ statements.
      - (xiv) **_while_ statement:**
      it replaces _while_ statements with _do_ statements.
    - (c) Others
      - (i) **OO-specific:**
      the mutation operators related to O(bject)-O(riented) Programming features[[4]](#ref4), such as Encapsulation, Inheritance and Polymorphism, e.g. _super_ keyword insertion.
      - (ii) **SQL-specific:**
      the mutation operators related to SQL-specific features[[6]](#ref6), e.g. replacing _SELECT_ to _SELECT DISTINCT_.
      - (iii) **Java-specific<sup>[6](#myfootnote6)</sup>:**
      the mutation operators related to Java-specific features[[4]](#ref4) (the operators in Java-Specific Features), e.g. _this_ keyword insertion.
      - (iv) **JavaScript-specific:**
      the mutation operators related to JavaScript-specific features[[4]](#ref4) (including DOM, JQUERY, and XmlHttpRequest operators), e.g. _var_ keyword deletion.
      - (v) **SpreadSheet-specific:**
      the mutation operators related to SpreadSheet-specific features[[7]](#ref7), e.g. changing range of cell areas.
      - (vi) **AOP-specific:**
      the mutation operators related to A(spect)-O(riented)-P(rogramming) features[[8]](#ref8)[[9]](#ref9), e.g. removing pointcut.
      - (vii) **concurrent mutation:**
      the mutation operators related to concurrent programming features[[10]](#ref10)[[11]](#ref11), e.g. replacing _notifyAll()_ with _notify()_.
      - (viii) **Interface mutation:**
      the mutation operators related to Interface-specific features[[12]](#ref12)[[13]](#ref13)}, suitable for use during integration testing.

## Footnotes:

<a name="myfootnote1">1</a>:The syntax of these operators might vary slightly in different languages. Here we just used the operators in Java as an example. So as the same in (a.ii) - (a.vi) operators.

<a name="myfootnote2">2</a>:The definition of this operator is from the Mothra[[14]](#ref14).

<a name="myfootnote3">3</a>:The types of the variables varies in different programming languages.

<a name="myfootnote4">4</a>:The changes between the objects of the parent and the child are excluded which belongs to "OO-specific".

<a name="myfootnote5">5</a>:To maintain the syntactical validity of the mutants, semicolons or other symbols, such as _continue_ in Fortran, are retained.

<a name="myfootnote6">6</a>:This set of mutation operators originated from Java features but not limited to Java language, since other languages can share certain features, e.g., _this_ keyword is also available in C++ and C#, and _static_ modifier is supported by C and C++ as well.

# References
<a name="ref1">[1]</a>: Ma YS, Offutt J, Kwon YR. Mujava:a mutation system for java. Proceedings of the 28th international conference on Software engineering, ACM, 2006; 827–830.

<a name="ref2">[2]</a>: Available mutation operations (PIT). http://pitest.org/quickstart/mutators/. [Online; accessed 10-August-2016].

<a name="ref3">[3]</a>: Ma YS, Offutt J. Description of method-level mutation operators for java. Electronics and Telecommunications
Research Institute, Korea, Tech. Rep 2005; .

<a name="ref4">[4]</a>: Ma YS, Offutt J. Description of class mutation mutation operators for java. Electronics and Telecommunications
Research Institute, Korea, Tech. Rep 2005; .

<a name="ref5">[5]</a>: Agrawal H, DeMillo R, Hathaway R, Hsu W, Hsu W, Krauser E, Martin RJ, Mathur A, Spafford E. Design of
mutant operators for the c programming language. Technical Report, Technical Report SERC-TR-41-P, Software
Engineering Research Center, Department of Computer Science, Purdue University, Indiana 1989.

<a name="ref6">[6]</a>: Tuya J, Su&#225;rez-Cabal MJ, De La Riva C. Mutating database queries. Information and Software Technology 2007; 49(4):398–417.

<a name="ref7">[7]</a>: Außerlechner S, Fruhmann S, Wieser W, Hofer B, Spo ̈rk R, Mu ̈hlbacher C, Wotawa F. The right choice matters! smt solving substantially improves model-based debugging of spreadsheets. 2013 13th International Conference
on Quality Software, IEEE, 2013; 139–148.

<a name="ref8">[8]</a>: Delamare R, Baudry B, Ghosh S, Gupta S, Le Traon Y. An approach for testing pointcut descriptors in aspectj. Software Testing, Verification and Reliability 2011; 21(3):215–239.

<a name="ref9">[9]</a>: Xu D, Ding J. Prioritizing state-based aspect tests. 2010 Third International Conference on Software Testing, Verification and Validation, IEEE, 2010; 265–274.

<a name="ref10">[10]</a>: Hong S, Staats M, Ahn J, Kim M, Rothermel G. The impact of concurrent coverage metrics on testing effectiveness. Software Testing, Verification and Validation (ICST), 2013 IEEE Sixth International Conference on, IEEE, 2013; 232–241.

<a name="ref11">[11]</a>: Hong S, Staats M, Ahn J, Kim M, Rothermel G. Are concurrency coverage metrics effective for testing: a comprehensive empirical investigation. Software Testing, Verification and Reliability 2015; 25(4):334–370.

<a name="ref12">[12]</a>: Hou SS, Zhang L, Xie T, Mei H, Sun JS. Applying interface-contract mutation in regression testing of component-based software. Software Maintenance, 2007. ICSM 2007. IEEE International Conference on, IEEE, 2007; 174– 183.

<a name="ref13">[13]</a>: Yoon H, Choi B. Effective test case selection for component customization and its application to enterprise javabeans. Software Testing, Verification and Reliability 2004; 14(1):45–70.

<a name="ref14">[14]</a>: King KN, Offutt AJ. A fortran language system for mutation-based software testing. Software: Practice and Experience 1991; 21(7):685–718.