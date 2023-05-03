Download Link: https://assignmentchef.com/product/solved-cs-754-assignment-3
<br>
Advanced Image Processing




Remember the honor code while submitting this (and every other) assignment. All members of the group should work on and <u>understand</u> all parts of the assignment. We will adopt a zero-tolerance policy against any violation.

Submission instructions: You should ideally type out all the answers in Word (with the equation editor) or using Latex. In either case, prepare a pdf file. Create a single zip or rar file containing the report, code and sample outputs and name it as follows: A3-IdNumberOfFirstStudent-IdNumberOfSecondStudent.zip. (If you are doing the assignment alone, the name of the zip file is A3-IdNumber.zip). Upload the file on moodle BEFORE 11:55 pm on the due date. The cutoff (beyond which no submission will be accepted) is mentioned on moodle. Note that only one student per group should upload their work on moodle. Please preserve a copy of all your work until the end of the semester. <u>If you have difficulties, please do not hesitate to seek help from </u>me.

<ol>

 <li>Download the book ‘Statistical Learning with Sparsity: The Lasso and Generalizations’ from <a href="https://web">https://web</a>. <a href="http://stanford.edu/~hastie/StatLearnSparsity_files/SLS_corrected_1.4.16.pdf,">stanford.edu/~hastie/StatLearnSparsity_files/SLS_corrected_1.4.16.pdf</a><u>,</u> which is the website of one of the authors. (The book can be officially downloaded from this online source). Your task is to trace through the steps of the proof of Theorem 11.1(b). This theorem essentially derives error bounds on the</li>

</ol>

minimum of the following objective function: J(β) = 2N Iy – XβI<sup>2</sup> + ANIβI1 where AN is a regularization

1

parameter, β E Rp is the unknown sparse signal, y = Xβ + w is a measurement vector with N values, w is a zero-mean i.i.d. Gaussian noise vector whose each element has standard deviation a and X E R<sup>N×</sup>p is a sensing matrix whose every column is unit normalized. This particular estimator (i.e. minimizer of J(x) for x) is called the LASSO in the statistics literature. The theorem derives a statistical bound on A also. Your task is split up in the following manner:

<ul>

 <li>Define the restricted eigenvalue condition (the answer’s there in the book and you are allowed to read it, but you also need to <u>understand</u> it).</li>

 <li>Starting from equation 11.20 on page 309 – explain why G(ˆv) &lt; G(0).</li>

 <li>Do the algebra to obtain equation 11.21.</li>

 <li>Do the algebra in more detail to obtain equation 11.22 (state the exact method of application of Holder’s inequality – check the wiki article on it, if you want to find out what this inequality states).</li>

 <li>Derive equation 11.23.</li>

 <li>Assuming Lemma 11.1 is true and now that you have derived equation 11.23, complete the proof for the final error bound for equation 11.14b.</li>

 <li>In which part of the proof does the bound AN &gt; <sub>2</sub><u>IX</u><u><sup>T</sup></u> wI<u>∞</u> show up? Explain.</li>

</ul>

N

<ul>

 <li>Why is the cone constraint required? You may read the rest of the chapter to find the answer.</li>

 <li>Read example 11.1 which tells you how to put a tail bound on AN assuming that the noise vector w is zero-mean Gaussian with standard deviation a. Given this, state the advantages of this theorem over Theorem 3 that we did in class. You may read parts of the rest of the chapter to answer this question. What are the advantages of Theorem 3 over this particular theorem?</li>

</ul>




<ul>

 <li>Now read Theorem 1.10 till corollary 1.2 and comments on it concerning an estimator called the ‘Dantzig selector’, in the tutorial ‘Introduction to Compressed Sensing’ by Davenport, Duarte, Eldar and Kut­ You can find it here: <a href="http://www.ecs.umass.edu/~mduarte/images/IntroCS.pdf">http://www.ecs.umass.edu/~mduarte/images/IntroCS.pdf</a>. What is the common thread between the bounds on the ‘Dantzig selector’ and the LASSO?</li>

 <li>Read the abstract and introduction (section 1) of the paper ‘Square-root lasso: pivotal recovery of sparse signals via conic programming’ by Belloni et al, published in the journal Biometrika. See https: //<a href="https://www.jstor.org/stable/23076172">jstor.org/stable/23076172</a>. This paper proposes an estimator called the square-root LASSO. What is the advantage of the square-root LASSO over the LASSO? [2 x 8 + 6 + 4 + 4 = 30 points]</li>

</ul>

<ol start="2">

 <li>In this task, you will you use the well-known package L1 LS from <a href="https://stanford.edu/~boyd/l1_ls/">https://stanford.edu/~boyd/l1_ls/</a><u>.</u> This package is often used for compressed sensing solution, but here you will use it for the purpose of tomographic reconstruction. The homework folder contains images of two slices taken from an MR volume of the brain. Create measurements by parallel beam tomographic projections at any 18 randomly angles chosen from a uniform distribution on [0, π). Use the MATLAB function ‘radon’ for this purpose. Now perform tomographic reconstruction using the following method: (a) filtered back-projection using the Ram­Lak filter, as implemented in the ‘iradon’ function in MATLAB, (b) independent CS-based reconstruction for each slice by solving an optimization problem of the form J(x) = Iy – AxI<sup>2</sup> + λIxI1, (c) a coupled CS-based reconstruction that takes into account the similarity of the two slices using the model given in the lectures notes on tomography. For parts (b) and (c), use the aforementioned package from Stanford. For part (c), make sure you use a <u>different</u> random set of 18 angles for each of the two slices. The tricky part is careful creation of the forward model matrix A or a function handle representing that matrix, as well as the corresponding adjoint operator A<sup>T</sup>. Use the 2D-DCT basis for the image representation. Modify the objective function from the lecture notes for the case of three similar slices. Carefully define all terms in the equation and re-implement it. [3+7+8+7 = 25 points]</li>

 <li>Prove the following properties of the Radon transform:</li>

</ol>

<ul>

 <li>Shifting: R(g(x – x0,y – y0))(p,θ) = R(g(x,y))(p – x0 cosθ – y0 sinθ,θ). Here p is the offset and θ is the angle of projection.</li>

 <li>Rotation: Let g<sup>‘</sup>(r, ) = g(r, – 0). Then prove that R(g<sup>‘</sup>)(p, θ) = R(g)(p, <sub>0</sub> – θ).</li>

 <li>Convolution: Given image f(x, y) and kernel k(x, y), show that Rθ(f *k) = Rθ(f)*Rθ(k), where * is the convolution operation. In other words, the Radon transform of the convolution of two signals is equal to the convolution of the Radon transform of the individual signals (in the same angles). [8+5+7=20 points]</li>

</ul>

<ol start="4">

 <li>For a sensing matrix with columns having unit magnitude, with s-order restricted isometry constant δ<sub>s</sub> and mutual coherence t, prove that δ<sub>s</sub> &lt; (s – 1)t. (Hint: Use Gershgorin’s disc theorem.) [10 points]</li>

 <li>Here is our Google search question again. You know of the applications of tomography in medicine (CT scanning) and virology/structural biology. Your job is to search for a journal paper from any <u>other</u> field which requires the use of tomographic reconstruction (examples: seismology, agriculture, gemology). State the title, venue and year of publication of the paper. State the mathematical problem defined in the paper. Take care to explain the meaning of all key terms clearly. State the method of optimization that the paper uses to solve the problem. [15 points]</li>

</ol>