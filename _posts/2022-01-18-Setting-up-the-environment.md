---
toc: true
layout: post
description: Installing conda and creating a new environment.
categories: [markdown]
title: Setting up the environment
---

If you already have anaconda/conda/miniconda/conda-forge, proceed to step 7.

**Step 1.** Download conda installer.

```
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/miniconda.sh
```

**NOTE 1a:** if this fails with "wget: command not found" install wget via "sudo apt install wget" (Ubuntu)
or "brew install wget" (MacOS). Then try to do step 1 again.

**NOTE 1b:** alternatively, you can just follow the link above using your browser and download the file this way.

**Step 2.**  Install miniconda.

```
bash ~/miniconda.sh
```

**Step 3.** Read and accept all licences.
**Step 4.** When asked where to install conda, just press enter to install it in the default directory.
**Step 5.** **IMPORTANT:** Then it will ask you "Do you wish the installer to initialize Miniconda3". Type "yes" and press enter.
**Step 6.** **IMPORTANT:** Restart your terminal session – open and close your terminal window.

**NOTE:** If you don't want conda to start base envorinment in every terminal you open, you can execute `conda config --set auto_activate_base false`.

**Step 7.** Create a new environment `nlp_class` with python 3.7.

```
conda create --name nlp_class python=3.7
```

**NOTE:** If you have `conda not found` error, it might mean you skipped step 5 and now need to add conda to your `PATH` manually. It it easy to do, here's [a solution](https://stackoverflow.com/questions/35246386/conda-command-not-found).

**Step 8.** Activate this environment.

```
conda activate nlp_class
```

**Step 9.** Install required libraries.

```
python -m pip install jupyterlab torch transformers datasets scikit-learn
```

**Step 10.** Install a new kernel to a jupyter lab.

```
python -m ipykernel install --name nlp_class
```

**NOTE:** If step 10 fails, ask Vlad for help.

**Step 11.** Launch jupyter lab.

```
jupyter lab
```

This should open a browser tab with Jupyter Lab running.

**Step 12.** On the right, you will see a couple of available notebook enviornments under "Notebook" title.
Select "nlp_class" and create a new notebook.

**Step 13.** Make sure all imports work. To do this execute the following code.

```python
import torch
import sklearn
import transformers
import datasets
```

If this fails, ask Vlad for help.


Now you should be good to go. If you are wondering why we need conda and environments, you can read [this blogpost](https://realpython.com/python-virtual-environments-a-primer/).
