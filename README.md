# riscv_ctb_challenges
## Challenge Level 1
**Logical :**\
<img width="330" alt="Screenshot 2566-07-28 at 15 26 10" src="https://github.com/vyomasystems-lab/riscv-ctb-challenge-PatNJ18/assets/88830316/61b7b5ba-ec5c-4f0c-b842-9a16564081d0">

There is an error in assembly code which use wrong register name "z4" instead "s4"

![Screenshot 2566-07-30 at 11 51 11](https://github.com/vyomasystems-lab/riscv-ctb-challenge-PatNJ18/assets/88830316/b671001b-1e3f-47ca-9bb3-8aaaabaddbc8)

so we fix it with change an incorrect name register to s4


**Loop :** 

There is an infinite loop in assembly code at line 22. 

![Screenshot 2566-07-30 at 11 38 08](https://github.com/vyomasystems-lab/riscv-ctb-challenge-PatNJ18/assets/88830316/eb5b8b57-2d79-4af6-8255-74b24c245994)

Which has one condition to check if answers from input equal in the test cases.


But there is another condition need to check is if it is going to last test cases yet?

![Screenshot 2566-07-30 at 11 38 20](https://github.com/vyomasystems-lab/riscv-ctb-challenge-PatNJ18/assets/88830316/67e6d472-6b11-4866-97fb-c68e24202ce0)

To fix infinite loop we add 2 instructions first is a counter use t6 which start as 0 and add 1 every test case input,

Then we check if t6 equal number of our test cases yet then jump instruction to test_end


**Illegal Instruction :**

There is an illegal instruction which cause by `.word 0`. Then it is handler with mtvec handler which is use to detect if there is a illegal instruction occur.

The bug is after it handler the illegal instruction it still using old instruction address so it cause error again after that it repeatly handler process which cause an infinite loop.

![Screenshot 2566-07-30 at 12 00 26](https://github.com/vyomasystems-lab/riscv-ctb-challenge-PatNJ18/assets/88830316/2cea7350-1c33-40d3-9f76-586f26519070)


To fix this bug we add 2 instructions.

first is `addi t0, t0, 8` which increment pc by 8 it causes pc move 2 instruction from current instruction which cause illegal instruction.

second is `csrw mepc, t0` which write down our new pc to  mepc a register which provide an address for illegal instruction handler.

![Screenshot 2566-07-30 at 12 13 22](https://github.com/vyomasystems-lab/riscv-ctb-challenge-PatNJ18/assets/88830316/8b53bc45-0034-4c15-a2f1-f418e5b95122)



## Challenge Level 2

**Instructions :**

![Screenshot 2566-07-22 at 21 54 46](https://github.com/vyomasystems-lab/riscv-ctb-challenge-PatNJ18/assets/88830316/d7bd7d0b-91aa-4dd4-9b29-c9c8f8a133f3)

Error is there are instructions in the test generate by AAPG which is `divw` ,`remuw` ,`mulw` ,`remw` which doesn't recognize by risc-v model

![Screenshot 2566-07-30 at 15 49 29](https://github.com/vyomasystems-lab/riscv-ctb-challenge-PatNJ18/assets/88830316/e1e22cfe-b9c9-46d8-90b3-486194829de1)
![image](https://github.com/vyomasystems-lab/riscv-ctb-challenge-PatNJ18/assets/88830316/3835cbec-c175-4925-83f2-71a9f41e5717)

In distribution of test case there are rv64 instruction generate which is `rel_rv6m` to fix the bug we change 10 to 0. Which it shouldn't generate rv64 bit anymore.

**Exceptions :**

The YAML file can created manual or run make file then it will be created by command `aapg gen --config_file $(PWD)/rv32i.yaml --asm_name test --output_dir $(PWD) --arch rv32`.

After the file created we use previous challenge config file as a template and custom our desire in the exception generate section.

We want to produce 10 exceptions so first we specify a ecause[x] to a number we want some of ecause need in order to generate 10 exceptions.

![Screenshot 2566-07-30 at 16 27 16](https://github.com/vyomasystems-lab/riscv-ctb-challenge-PatNJ18/assets/88830316/c808abd1-f6c6-4528-8ec4-16938db1a910)

After we config a number of exceptions now we turn to pick instruction which is a test case. AAPG provide a random generate that pick a test instruction by config a ecause value in 

program-macao section to `"random"`.

![image](https://github.com/vyomasystems-lab/riscv-ctb-challenge-PatNJ18/assets/88830316/2fadd845-ac83-4368-86c9-382fdb175d2e)

After we config succesfully run `make` and we should see a 10 exceptions write to a exceptions.log or a output in terminal.

![Screenshot 2566-07-30 at 16 28 05](https://github.com/vyomasystems-lab/riscv-ctb-challenge-PatNJ18/assets/88830316/7870540e-0bbe-4449-9235-949f9612a098)


## Challenge Level 3

![image](https://github.com/vyomasystems-lab/riscv-ctb-challenge-PatNJ18/assets/88830316/e30fa833-89b1-4044-a986-04fc2035a335)




