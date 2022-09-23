## Using CiMPG for existing large proof scores of TLS 1.0
In this repository, you can find:

* `tls.cafe`: the specification of the protocol in CafeOBJ
* `proofscores` directory: contains the revised proof scores of all invariants
* `cmd-cimpg` directory: contains CiMPG commands for all invariants
* `generated-proofscripts` directory: contains the generated proof scripts by CiMPG for all invariants


## Tools installation
The verification requires CafeInMaude, which can be downloaded from here: https://github.com/ariesco/CafeInMaude.
To execute CafeInMaude, we first need to intall Maude, which we can download its version 3.2 from here: http://maude.cs.illinois.edu/w/index.php/Maude_download_and_installation.
For Maude, all you need to do is to download the binary file (and perhaps add the tool to the PATH environment variable to execute the tool from everywhere).
For CafeInMaude, you need to clone the repo.
After that, move to the next step to execute proof scores.

## Executing proof scripts
Once intalled CafeInMaude, you can try to run the proof scripts with CiMPA, a part of CafeInMaude. For example, to execute the proof script of `inv1`, we use the following commands:

```
maude -allow-files path-to-CafeInMaude/src/cafeInMaude.maude
load tls.cafe .
load generated-proofscripts/inv1.cafe .
```

where the first command starts the CafeInMaude environment (`path-to-CafeInMaude` is the path of the CafeInMaude folder),
the second command load the specification,
and the last command loads the proof scripts.
If nothing is wrong, when the execution finishes, you will see `Proof finished`, meaning that `inv1` is proved with that proof script. 
Note that you need to make sure that the paths are correct. You may need to use the absolute paths instead of the relative paths as above.


## Generating proof scripts
To re-generate the proof scripts, CiMPG is used with commands we already provided.
For example, to generate the proof script of `inv1` again, we use the following commands:

```
maude -allow-files path-to-CafeInMaude/src/cafeInMaude.maude
load cmd-cimpg/cmd1.cafe .
```

Again, you need to make sure that the paths are correct, for which you may need to use the absolute paths instead of the relative paths as above.
The second command loads all commands written before `eof` (end-of-file) symbol  in the `cmd1.cafe` file.
If some amount of time, CiMPG will generate the proof script of `inv1`, which is saved to the file located at `generated-proofscripts/inv1.cafe`.