# HW0_S25

## Getting Started
All the homeworks are distributed as Jupyter notebooks. Follow these instructions to get everything set up.

1. Install [Julia](https://julialang.org/) by running the one of the following terminal commands depending on your system. This will install the [Juliaup](https://github.com/JuliaLang/juliaup) installation manager. DO NOT install version-specific binaries.  
   a. for Windows, run `winget install julia -s msstore`, then `juliaup add lts` to install the LTS version, and `juliaup default lts` to set LTS as the default Julia version.
   
   b. for Mac/Linux, run `curl -fsSL https://install.julialang.org | sh -s -- -y --default-channel lts` to achive the same thing.
2. Clone this repo `git clone https://github.com/Optimal-Control-16-745/HW0_S25.git` or download the zip file.
3. Start a Julia REPL in your terminal using `julia`.
4. Install the [IJulia](https://github.com/JuliaLang/IJulia.jl) using the Julia package manager. In the REPL, enter the package manager using `]`, then enter `add IJulia` to add it to your system path.
5. In the REPL (hit backspace to exit the package manager), enter `using IJulia`.
6. Launch the notebook using `notebook()` or `jupyterlab()`.
7. (Optional) If you use VSCode, instead of steps 5-7, you can install the [Julia](https://code.visualstudio.com/docs/languages/julia) and [Jupyter](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.jupyter) extensions in VSCode. Make sure you set the `kernel` to `Julia lts channel` before running your code.

## HW Instructions 
1. Please watch the [HW0 + Julia Video Walkthrough](https://www.youtube.com/watch?v=RetAn_9AOMg) by [Kevin Tracy](https://kevintracy.info/) from last year and checkout the corresponding Jupyter notebook `julia_primer.ipynb`. Note: the video was made for the previous Julia LTS version(1.6.7) and we will be using the latest (and much improved) LTS, but the content is still very much relevant.
2. After you have completed the walk through, fill out `Q1.ipynb` and `Q2.ipynb`.

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

