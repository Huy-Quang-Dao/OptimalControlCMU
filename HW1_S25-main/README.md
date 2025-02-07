# HW1_S25

**Due 2/6 11:59 PM Eastern.**

## Instructions
NOTE: You should not use any while loops in this homework. All of these concepts can and should be implemented with for loops for multiple reasons. Using while loops for things like Newton's method and linesearches is more difficult for both you and the TA's to debug.

Fill out project proposal form: [https://forms.gle/NcbaNHSeNjTQa4e58](https://forms.gle/NcbaNHSeNjTQa4e58)

In this homework we are going to explore topics in dynamics and optimization. Here is an overview of the problems:

1. Implement 3 explicit and 3 implicit integrators to simulate a double pendulum and examine the differences in accuracy. The goal of this problem is to start thinking about integrators as modular, and demonstrate the difference between explicit and implicit integrators. 

2. Write a well structured implementation of Newton's method with a backtracking linesearch. You will use this function to solve a simple constrained optimization problem, then you will use it to solve for the motor torques and configuration for a quadruped to balance on one leg. 

3. Implement a Quadratic Program (QP) solver using the log-domain interior point method. This solver will then be used in a clever way to simulate a falling brick as it makes contact with the floor. 

4. Fill out project proposal form: [https://forms.gle/NcbaNHSeNjTQa4e58](https://forms.gle/NcbaNHSeNjTQa4e58)

## Submission Instructions

Submit all HWs as **PDFs of your completed Jupyter Notebooks in [Gradescope](https://www.gradescope.com/courses/952874)**. Please review all the checklist items and instructions below:

### Checklist

Before you submit your completed homework PDF, remember to complete **all** the checklist items below:

- Make sure text and code, including special characters, are completely legible.
- Make sure code is completely visible (i.e., no cropped lines). If we can't see it, then we can't grade it... Look at section below for details on how to remedy this.
- Make sure plots and unit tests have been outputted and rendered properly. **Meshcat** visuals are **exempt**.
- DO NOT ALTER UNIT TEST CASES. We check and can tell...
- Assign questions to **each respective page** of your PDF in [Gradescope](https://www.gradescope.com/courses/952874), including the text of the problem.

### Fixing Cropped Code

If your code is cropped in the PDF, then there are multiple remedies for this:

1. **Split line around binary operator (e.g., +)**:
```
L_grad = FD.gradient(f, x) +
                transpose(FD.jacobian(c, x))*λ
```
2. **Split line around parenthesis**:
```
L_grad = (FD.gradient(f, x)
                + transpose(FD.jacobian(c, x))*λ)
```
3. **Split line after assignment operator (e.g., =)**:
```
L_grad = 
    FD.gradient(f, x) + transpose(FD.jacobian(c, x))*λ
```
4. **Combine 1-3 to split into more lines**:
```
L_grad = 
    FD.gradient(f, x) +
    transpose(FD.jacobian(c, x))*λ
```

5. **Assign terms to more variables**:
```
cost_grad = FD.gradient(f, x)
constraint_jac_T = transpose(FD.jacobian(c, x))

L_grad = cost_grad + constraint_jac_T*λ
```

### Export to PDF

Feel free to use any method you'd like to export your Jupyter notebook as a PDF (**with all checklist items completed**). 

We recommend the following method of converting your Jupyter notebook to a PDF because it requires no additional installs (hopefully). It's slightly involved, but it is the most consistent in our experience.

1. Open the Jupyter notebook in your favorite **web browser** (not VS Code) with [IJulia](https://github.com/JuliaLang/IJulia.jl).
2. Go through the **submission checklist**, and make sure **all** relevant items are completed.
3. In the top left corner of the Jupyter menu bar, do `File -> Save and Export Notebook As -> HTML`. It should download an HTML file.
4. Open the downloaded HTML file in your favorite web browser.
5. Open up the browser's print menu and select `Save as PDF`.
6. Save and [combine](https://www.adobe.com/acrobat/online/merge-pdf.html) PDFs. 
7. Submit on **[Gradescope](https://www.gradescope.com/courses/952874)**, and make sure to **assign the right pages** to all questions.

### Others

If HTML to PDF does not work, feel free to try other methods: [https://mljar.com/blog/jupyter-notebook-pdf/](https://mljar.com/blog/jupyter-notebook-pdf/).



## Notes 

- These questions will have long outputs for each cell, remember you can use `cell -> all output -> toggle scrolling` to better see all of the output without having to scroll. 
