# morpheus

Summer Python project for senior undergraduate students (2019-2020) @ ETTI, UPB.

### Project milestones:

0. Set up a work environment ("[**Project setup**](https://github.com/SRBNM/morpheus/tree/master#project-setup)" section) and get the hang of the work procedure ("[**Work procedure**](https://github.com/SRBNM/morpheus/tree/master#work-procedure)" section).

1. Build a database of normal speech and (authentic) growled speech (**NAG**).

2. Implement the voice morphing algorithm (**VMA**) proposed in \[1\].

3. Develop a SVM classifier (**Baseline**), to distinguish between authentic and morphed growls.

4. Develop a deep feedforward neural network classifier (**DNN**), to distinguish between authentic and morphed growls.

[\[1\] J. Bonada and M. Blaauw, "Generation of growl-type voice qualities by spectral morphing," in Proc. of the 2013 IEEE International Conference on Acoustics, Speech and Signal Processing (ICASSP), Vancouver, Canada, pp. 6910-6914, May 2013](https://ieeexplore.ieee.org/abstract/document/6639001)

### Project details:

1. **NAG**:
   - The final database will contain 3 speech classes: Normal and Growled_A (authentic) + Growled_M (morphed).
   - For the first two classes, 10 speakers must be used.
   - For each speaker, 10 utterances must be recorded (the same for all speakers).
   - All files must be recorded at 16 kHz sampling rate, using PCM format (_.wav_), and must be around 3 seconds long.
   - As a software example, [Audacity](https://www.audacityteam.org/download) can be used.
   - Each audio file should be saved using the following naming convention: "CCSSUU.wav", where CC is the class identifier ('NN' or 'GA'), SS is the speaker number ('01' ... '10') and UU is the utterance number ('01' ... '10'); e.g: _NN0201.wav_ -- Normal speech, 2nd speaker's 1st utterance.
   - For each audio file, an identically named Excel file (_.xlsx_) must be created, in which to log additional information: speaker gender, age, and musical training (especially concerning growling vocals).
   - After applying the voice morphing algorithm, the processed audio data will be saved in files following the same naming convention, but with the 'GM' class identifier.

2. **VMA**:
   - Complete implementation (**_details to follow_**).

3. **Baseline**:
   - The baseline system will consist of a [SVM](https://scikit-learn.org/stable/modules/svm.html) classifier (**_details to follow_**).
   - In separate trials, it will be trained and tested using the following extracted feature sets:
     * MFCC
     * MFCC and delta coefficients
     * MFCC, delta coefficients, and delta-delta coefficients.

4. **DNN**:
   - The proposed system will be a deep feedforward (dense) neural network using multilayer perceptrons ([MLP](https://keras.io/layers/core/)) (**_details to follow_**).
   - The extracted features will be the same as in the three baseline sets (in separate trials).

5. Other notes:
   - The train/dev/test split will be 40%/30%/30%.
   - The metrics used for performance assessment and comparison will be: Accuracy, Precision and Avg. Precision, Recall and Avg. Recall, F1-measure and Avg. F1-measure.
   - In addition, the following graphical results are required: confusion matrices, and validation error and accuracy evolution in time.
   - In the final stage, a **4-page** paper (using the [IEEE Word template](https://www.ieee.org/content/dam/ieee-org/ieee/web/org/conferences/Conference-template-A4.doc)) will be written to clearly, convincingly, and eloquently present the project and how it relates to the wider scope of voice morphing and machine learning research.
   - Structure:
     * Abstract
     * S1. Introduction
     * S2. Proposed System Architecture
     * S3. Implementation Details
     * S3.1. The NAG Database
     * S3.2. Extracted Features
     * S3.3. Implementation Details
     * S4. Experimental Setup and Results
     * S4.1. Experimental Setup Details
     * S4.2. Experimental Results
     * S5. Conclusions
     * References

### Project setup:

0. Make sure your operating system architecture is **64-bit**!

1. Install [Anaconda for Python 3](https://www.anaconda.com/distribution/).

2. (_If using Windows, launch Anaconda Prompt as Admin._) Set up a new virtual environment, named _morpheus_:
```
conda create -n morpheus python=3.6 tensorflow keras scikit-learn pandas matplotlib graphviz spyder
conda info --envs
```

3. Activate the _morpheus_ environment:
```
conda activate morpheus
conda info --envs
```

4. Install the [python_speech_features](https://python-speech-features.readthedocs.io/en/latest/) package:
```
pip install python-speech-features
conda list
```

5. Register a [GitHub account](https://github.com).

6. Fork (_copy_) the **original** [_morpheus_ repository](https://github.com/SRBNM/morpheus) by clicking on the **Fork** button in the top right corner.

7. Install [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

8. (_If using Windows, launch Git Bash._) Configure _git_ (_Hint: you can always use the_ **git --help** _command_):
```
git config --global user.email "<email_address>"
(e.g: <email_address> = smihalache@gmail.com   <--- use the same email as for your GitHub account)
git config --global user.name "<name>"
(e.g: <name> = SRBNM   <--- use the same name as for your GitHub account)
```

9. Navigate to your desired work folder path (_Hint: you can always use the_ **ls -a** _command to list all files in the current directory_):
```
cd <path>
(e.g: cd "/c/summer_project/")
```

10. Clone (_download_) the **forked** _morpheus_ repository (_your copy_) and add a remote (_alias_) to the **original** one (_Hint:_ **origin** _is the name of the remote of_ **your** _repository_):
```
git clone https://github.com/SRBNM2/morpheus.git
git remote add morpheus https://github.com/SRBNM/morpheus.git
git remote -v
```

11. Switch to your repository directory (_Hint: Notice the_ **(master)** _marker_):
```
cd morpheus
```

12. Launch Spyder from the Anaconda virtual environment (_morpheus_):
```
spyder
```

13. From the **Project** menu, select **New Project...**. Select **Existing directory** and browse for the _<path>_ used at step 11 (e.g: "_C:\summer_project\morpheus_"). Create a new file and save it with the **.py** extension (e.g: **main.py**).

14. Update your **remote** fork with all **local** changes:
```
git checkout master
git add --all
git commit -m "<short_description>"
(e.g: <short_description> = first update   <--- to explain what is being changed)
git push origin master
```

### Work procedure

1. Update your **local** fork from the **original** repository:
```
cd <path>/morpheus
git pull morpheus master
```

2. Activate the Anaconda _morpheus_ virtual environment and launch Spyder.

3. After finishing coding, update your **remote** fork with all **local** changes.

### Software and code resources:

- Anaconda3 (with Spyder IDE)
- GitHub
- TensorFlow
- NumPy
- SciPy
- SciKit Learn
- Pandas
- Matplotlib
- h5py
- Graphviz
- Keras
- python_speech_features
