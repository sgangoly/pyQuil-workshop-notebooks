# pyQuil-workshop-notebooks

These notebooks were originally crafted by Sohaib Alam ([@msohaibalam](https://github.com/msohaibalam)) for a private pyQuil workshop. He allowed me to edit his slides and the accompanying notebooks found here. Thanks, Sohaib!

If you run into any issues with the instructions below, please feel free to open an issue or, better yet, email support@rigetti.com explaining your problem, including as much detail as possible, and we'll get back to you ASAP.

## Downloading pyQuil and the Forest™ SDK

The instructions for downloading pyQuil and the Forest™ SDK can be found on the [Installation and Getting Started] (https://pyquil.readthedocs.io/en/stable/start.html) page in our pyQuil docs.
If you can make it all the way to the end of this page and run the code at the bottom, then you will have successfully installed pyQuil and the Forest™ SDK, and you will be prepared to run all the notebooks for the workshop.
The notebooks can be found in the [`ipython-notebooks/`](https://github.com/amyfbrown/pyQuil-workshop-notebooks/tree/master/ipython-notebooks) directory.

### Downloading the Forest™ SDK

You can sign up to receive an email containing a download link for the Forest™ SDK for Windows (.msi), MacOS (.pkg), and Linux (.deb, .rpm) [here](http://rigetti.com/forest). **Don't click the "Sign up" button in the upper-right corner of the page, as that will sign you up for Quantum Cloud Services (QCS) instead of the SDK** (QCS is rad, but we have to walk before we can run). Instead, scroll down until you see a sign up form beneath "Download the new Forest™ SDK," and sign up there. You should then receive an email with the subject line "Download the new Forest SDK (beta)" from "Rigetti."

**NB**: If you do not receive the aforementioned email, it is likely you signed up for QCS by mistake. Try scrolling farther down the page to find the sign up form underneath "Download the new Forest™ SDK."

Next, download the appropriate file for your operating system, referring to the [OS-specific SDK download instructions](https://pyquil.readthedocs.io/en/stable/start.html#downloading-the-qvm-and-compiler) as necessary.

You'll know you have successfully downloaded the SDK when you can run `quilc -S` in a terminal window and get the following output:

```
amy@amy-macbook:~ $ quilc -S
+-----------------+
|  W E L C O M E  |
|   T O   T H E   |
|  R I G E T T I  |
|     Q U I L     |
| C O M P I L E R |
+-----------------+
Copyright (c) 2016-2019 Rigetti Computing.

This is a part of the Forest SDK. By using this program
you agree to the End User License Agreement (EULA) supplied
with this program. If you did not receive the EULA, please
contact <support@rigetti.com>.
```

This starts the Quantum Instruction Language Compiler (QUILC) server, and `qvm -S` starts the Quantum Virtual Machine (QVM) server. **You'll need [both of these servers](https://pyquil.readthedocs.io/en/stable/start.html#setting-up-server-mode-for-pyquil) running to simulate or run any pyQuil program.**

### Installing pyQuil

You can install pyQuil through [pip](https://pyquil.readthedocs.io/en/stable/start.html#upgrading-or-installing-pyquil) or conda, or you can clone it directly from our [GitHub repository](https://github.com/rigetti/pyquil).

You can check that you've successfully installed pyQuil by [starting your QUILC and QVM servers](https://pyquil.readthedocs.io/en/stable/start.html#setting-up-server-mode-for-pyquil), opening up a Python shell, and running the following brief program (found in the [Installation and Getting Started] (https://pyquil.readthedocs.io/en/stable/start.html) page):

```
from pyquil import Program, get_qc
from pyquil.gates import *

# construct a Bell State program
p = Program(H(0), CNOT(0, 1))

# run the program on a QVM
qc = get_qc('9q-square-qvm')
result = qc.run_and_measure(p, trials=10)
print(result[0])
print(result[1])
```

You should get out two identical bitstrings

```
>>> print(result[0])
[0 0 1 1 0 1 1 0 0 0]
>>> print(result[1])
[0 0 1 1 0 1 1 0 0 0]
```

The most common error encountered when trying the above looks like this:

```
ConnectionError: HTTPConnectionPool(host='localhost', port=5000): Max retries exceeded with url: /qvm (Caused by NewConnectionError('<urllib3.connection.HTTPConnection object at 0x112cf1390>: Failed to establish a new connection: [Errno 61] Connection refused',))
```

You can fix this by starting your [QUILC and QVM servers](https://pyquil.readthedocs.io/en/stable/start.html#setting-up-server-mode-for-pyquil). After that, the code should run. If you run into any other issues, please send an email to support@rigetti.com.

## Running the notebooks

You'll need to be able to run ipython notebooks to get the most out of the interactive poritons of the workshop. I personally use [Jupyter](https://jupyter.org/install), but anything that can run an ipython notebook will do.

Again, the workshop notebooks can be found in the [`ipython-notebooks/`](https://github.com/amyfbrown/pyQuil-workshop-notebooks/tree/master/ipython-notebooks) directory.

## Acknowledgements

As stated up top, my colleague Sohaib created the slides and notebooks for the pyQuil workshop, and he's generously allowed me to edit them for time and content for various presentations.
