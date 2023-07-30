# riscv_ctb_challenges
## Challenge Level 1
**Logical :**\
<img width="330" alt="Screenshot 2566-07-28 at 15 26 10" src="https://github.com/vyomasystems-lab/riscv-ctb-challenge-PatNJ18/assets/88830316/61b7b5ba-ec5c-4f0c-b842-9a16564081d0">

<p> There is an error in assembly code which use wrong register name "z4" instead "s4" </p>

![Screenshot 2566-07-30 at 11 51 11](https://github.com/vyomasystems-lab/riscv-ctb-challenge-PatNJ18/assets/88830316/b671001b-1e3f-47ca-9bb3-8aaaabaddbc8)
<p>
  so we fix it with change an incorrect name register to s4
</p>

**Loop :** 

<p>There is an infinite loop in assembly code at line 22. </p> 

![Screenshot 2566-07-30 at 11 38 08](https://github.com/vyomasystems-lab/riscv-ctb-challenge-PatNJ18/assets/88830316/eb5b8b57-2d79-4af6-8255-74b24c245994)
<p>Which has one condition to check if answers from input equal in the test cases.</p>
<p>But there is another condition need to check is if it is going to last test cases yet?</p>

![Screenshot 2566-07-30 at 11 38 20](https://github.com/vyomasystems-lab/riscv-ctb-challenge-PatNJ18/assets/88830316/67e6d472-6b11-4866-97fb-c68e24202ce0)

<p>To fix infinite loop we add 2 instructions first is a counter use t6 which start as 0 and add 1 every test case input,</p>
<p>Then we check if t6 equal number of our test cases yet then jump instruction to test_end</p>



