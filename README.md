# Latex Template for BracU CSE250 Exams
This template uses the $\rm\LaTeX$ [documentclass called `exam`](https://math.mit.edu/~psh/exam/examdoc.pdf) 
to automatically add up marks for all the questions and bonus questions. 
Summarized instructions for creating a question:

## Adding questions
Inside [`questions/`](/questions/) folder, create a new `.tex` file numbered from `1` (or `01`) to `99`. 
Any skipped file number will automatically be filled sequentially.

Each `.tex` file should contain a `\titledquestion` or `\bonustitledquestion`. Each such questions may contain parts and subparts:

```latex
questions
├── \titledquestion
│   ├── \part
│   │   ├── \subpart
│   │   │   ├── \subsubpart
│   │   │   └── \bonussubsubpart
│   │   └── \bonussubpart
│   └── \bonuspart
└── \bonustitledquestion
    └── \bonuspart
        ├── \bonussubpart
        │   └── \bonussubsubpart
        └── \bonussubpart
```

## Set-specific questions
If you want to have different questions for each set, you may create folders for them. For example, [`questions/A/01.tex`](/questions/A/01.tex) will replace (or add) [`questions/01.tex`](/questions/01.tex) for set `A`.

## CO/PO Mapping
For mapping course/program outcome (CO/PO) with a question, please use `\titledquestion{CO1}` and `\bonustitledquestion{CO2}` 
Formatting for these are defined in [`main.tex`](/main.tex) with `\qformat` and `\bonusqformat`.

## Marks
Marks/points to each question or part of a question can be allotted using an optional argument. 
In case you prefer it, there is a built-in `\half` macro for using $\tfrac{1}{2}$ instead of $.5$.
<table><tr><td>
<div style="width:300px">

```latex
\titledquestion{CO1}[2\half]
```
<\div>
</td><td>
<img width="268" alt="image" src="https://user-images.githubusercontent.com/67824850/217041237-76c9a734-221b-478c-aa12-92f76052826d.png">
</td></tr></table>

## Exam Question Set
You can specify the set (e.g. $\rm A$, $\rm B$ etc.) by defining `\setnum` in [`main.tex`](/main.tex). 
If not defined or commented, set will not appear in the question header.
<table><tr><th>
Command
</th><th>
First Page Header
</th><th>
Other Pages Header
</th></tr>
<tr><td>

```latex
\def\setnum{A}
```
</td><td>
<img width="515" alt="image" src="https://user-images.githubusercontent.com/67824850/217045404-5e7d78fe-6fa1-4016-9c77-06c3fff4e450.png">
</td><td>
<img width="515" alt="image" src="https://user-images.githubusercontent.com/67824850/217046231-4c25b87b-5348-4573-845b-f3d823081952.png">
</td></tr>
<tr><td>

```latex
% \def\setnum{A}
```
</td><td>
<img width="515" alt="image" src="https://user-images.githubusercontent.com/67824850/217045232-6ceb8cf5-9c7c-4115-8d8f-49d093e2e915.png">
</td><td>
<img width="510" alt="image" src="https://user-images.githubusercontent.com/67824850/217045755-9f2e37ea-bf29-4d44-a7de-75bf8ce4bfd9.png">
</td></tr></table>

## Course Section & Faculty Name
Just like the set, course section and faculty name can either be defined using `\sect` and `\faculty`, or can be omitted.

## Date of Exam
By default it uses current date on the question header and everywhere else (using `\today`). 
However, if the question should be printed some days later, it can be done by advancing by that amount of days in [`main.tex`](/main.tex). 
Negative numbers can also be used for using previous days.
By default it is set to `0`.
```latex
\advance\day by 0
```

## Solutions
[`exam`](https://math.mit.edu/~psh/exam/examdoc.pdf) documentclass supports directly 
by including solutions using `\solution`, `\solutionbox` etc. environments.
These can be shown by including `answers` argument in the documentclass declaration.

<table><tr><td>

```latex
\documentclass[a4paper, addpoints]{exam}
```
</td><td>
<img width="485" alt="image" src="https://user-images.githubusercontent.com/67824850/217028070-d8a10e83-78d2-497e-85fc-d67210c34e9a.png">
</td></tr>
<tr><td>

```latex
\documentclass[a4paper, addpoints, answers]{exam}
```
</td><td>
<img width="485" alt="image" src="https://user-images.githubusercontent.com/67824850/217027839-480caeb4-04fe-4390-88cc-7fa5683c6bfe.png">
</td></tr></table>
