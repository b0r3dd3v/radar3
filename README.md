This file is part of Quipper. Copyright (C) 2011-2019. Please see the
file COPYRIGHT for a list of authors, copyright holders, licensing,
and other details. All rights reserved.

======================================================================

The file bwt.qcl contains an implementation of the Binary Welded Tree
algorithm in Omer's quantum programming language QCL.

QCL is meant as a language to drive a quantum simulator, so it is a
bit tricky to get it to actually output a circuit; however, this can
be done with the right set of command line options. Essentially this
will cause the program to output a trace of the gates being simulated.

The following options were used to produce the file QCL-bwt-n4.out:

echo "dump a;" | \
qcl -i --log=y         \
      --test=n         \
      --check=n        \
      --dump-format=b  \
      --auto-dump=1    \
      --log-state=n    \
      --bits=64        \
      --show-regs=n    \
      --trunc-states=n \
      QCL-BWT-v1.qcl > QCL-bwt-n4.out

Finally, the program QCLParser, which is also contained in this
directory, can be used to import the circuit from QCL-bwt-n4.out 
into Quipper, where it can then be, for example, printed. To preview
the circuit in Quipper, do:

./QCLParser < QCL-bwt-n4.out
