java c
CE335 ASSIGNMENT 2023-2024 
(20% of the total module marks) 
Analysing Object Recognition and Attention Impairments in Alcoholics Using Visual Evoked Potential Signals 
Please read the following rules before you start: 
1. You should use only MATLAB for the code. 
2. Use the following file name format: firstname_lastname.m. 
3. There is no need of submitting the data files. 
4. Give instructions to run or compile your code at the top of your .m file in comment form, such as where the data files should be put and how to set parameters, etc. 
5. If your code doesn't run or compile after I follow your instructions, your work will be marked based on inspection of the program and you may get less than the full marks (perhaps  none). Thus,  it  is  your  job  to  make the instructions/comments clear and complete. 
6. You need to include results, such as figures, from running your program with different settings, explanations of the results, and discussion and suggestion on identifying most useful channels in your report. 
High-level problem description and objectives It is well known that excessive alcohol consumption affects certain mental activities and thus actions. This assignment is to analyse the visual evoked potential (VEP) signals recorded from alcoholics and non-alcoholics, so as to examine whether long term alcohol abuse has an effect on the speed and quality/strength of response in discrimination based mental tasks. Specifically, given hundreds of multi-channel VEP signal trials recorded from alcoholics and non-alcoholics respectively, you are asked to firstly calculate the amplitude and latency time of the P300 component (detailed explanation is given in the next section) in each trial and each channel, and then calculate and compare the average P300 amplitude and latency time of the alcoholics and those of the non-alcoholics. The VEP signals are noisy in general; therefore noise filtering is needed before the P300 peaks can be reliably detected and analysed.
After completing the assignment successfully, you should be able to conclude that long-term alcohol abuse causes impairments in object recognition.
Description of the experimental set-up used to record the VEPs (Background only) VEP data is recorded from 20 subjects (10 alcoholics and 10 non-alcoholics). Each subject completed 40 trials, therefore giving a total of 800 VEP signals. Measurements are taken for one second (the first second in each trial) from 64 electrodes placed on the subject’s scalp, which are sampled at 256 Hz. Therefore, a total of 256 data points are recorded from each electrode (channel) for each VEP signal.The VEP signals are recorded from subjects while being exposed to a single stimulus, which is a picture of an object chosen from the Snodgrass and Vanderwart picture set. These pictures are common black and white line drawings like kite, door, bolt, flag, etc. Figure 1 shows some of these pictures  and Figure 2 illustrates the presentation  of these pictures with the trial time  structure specified.

Figure 1: Some objects from Snodgrass and Vanderwart picture set 

Figure 2: Presentation of Snodgrass and Vanderwart picture stimulus The P300 (or P3) component is normally the third positive component within VEP, which normally occurs between 300 ms and 600 ms after the stimulus onset (e.g., the start of picture presentation). This component is evoked in a variety of decision-making tasks, and in particular when a stimulus is recognised.
Description of the VEP data 
You can download data files needed for this assignment from Moodle, which contains 800 .mat files with VEP signals, ca800.txt file with 800 filenames, and channel1.txt file with channel names.In ca800.txt, the first 400 names are for .mat files with VEP signals from 10 alcoholics, i.e., 40 files from each alcoholic subject, and the next 400 names are for .mat files with VEP signals from 10 non- alcoholics (controls), i.e., 40 files from each non-alcoholic subject.Here is an example of the file naming: a370_000.dat: The “a” means that the file is from an alcoholic, while the 370 denotes that the subject is named “370” and the last “000” denotes the trial number. Similarly, for a control (non-alcoholic) subject, the file name will start with ‘c’ .
The channel (i.e., electrode) list is in channel1.txt. Note that channels ‘X’, ‘Y’, and ‘nd’ are 3 reference channels which should be ignored in this assignment.To understand the data before you start programming, please load aXXX_XXX.mat file in Matlab, check the size of x, understand which dimension is for代 写CE335 ASSIGNMENT 2023-2024R
代做程序编程语言 channel and which for time (samples). You may also plot a VEP signal from a specific channel. 
Contact the module supervisor well before the deadline should you encounter any difficulties in downloading the zip file. 
The tasks 
I.    WRITE Mablab code to perform. the following tasks (be careful to follow the exact sequence of steps) and COMMENT your code properly:For each file/trial (i.e., each VEP signal) do the following. Repeat 800 times automatically to process ALL the files [Suggestion: use for loops  with fgetl to  read  the  filenames  from ca800.txt].
1. Load a VEP signal (size 64 x 256) from a .mat file. Make sure that the code can load the data into Matlab environment on any computer without needing to change a directory. [5 marks for automatically and correctly loading the 800 VEP signals] 
2.   Compute the VEP signal with reference to channel CZ, which is channel 16. That is, subtract channel  CZ  from  each  channel. After that, remove  channel  CZ  and the three reference channels, which are X (channel 32), nd (channel 63) and Y (channel 64). From now on, you have 60 channels to process in each trial. [3 marks] 
3.   Set the mean of each channel to zero (i.e., remove the mean of the signal from each channel). [2 marks] 
4.   a. For the first run: Do nothing in this step.
b. For the second run: Since P300 responses are band-limited to 8 Hz, filter the VEP signal using an appropriate minimum order Butterworth or Elliptic bandpass filter with passband from 2 Hz to 8 Hz and with stop frequencies at 0.5 Hz and  12 Hz.  Set the minimum  attenuation in the stopband to Rs=15 dB and passband ripple Rp=1 dB. You may use Matlab functions buttord and butter or ellipord and ellip to design the filter and filtfilt to implement the filter. [10 marks] 
c. For the third run: 
Do the same as in 4.b, but this time use an FIR filter instead of IIR filter. You may use Matlab functions kaiserord and fir1 to design the filter and conv to implement the filter.
You can refer to the teaching materials for lecture 8 and lab 4. [10 marks] [Note: In each run, do either a, b, or c in this step]
5. Compute the P300 peak amplitude and the corresponding latency time for each channel. You should have one amplitude value and one latency value for each channel (you may use one matrix for amplitude and one for latency). The P300 peak can be identified as the largest positive  peak  (there  could  be   several  peaks)  in  the  period  of  300-600  ms   (find  the corresponding sample points) after the stimulus onset (the start of a trial). If there are no peaks in this time period, set the P300 peak amplitude and latency to zero. [8 marks] After the above loops, do the following: 
1.  Calculate the average P300 amplitude and latency time of the alcoholic subjects in each channel (i.e., from the first 400 files) and the average P300 amplitude and latency time of the non-alcoholic subjects in each channel (i.e., from the last 400 files). [3 marks] 
2.  Compare the average P300 amplitudes of alcoholic subjects and non-alcoholic subjects in all the 60 channels using plot. [2 marks] 
3.  Compare the average P300 latencies of alcoholic subjects and non-alcoholic subjects in all the 60 channels using plot. [2 marks] 
II.  RUN your Matlab program
1.   Run your program without using bandpass filter (step 4.a). Record/save the results/figures.
2.   Run your program using step 4.b. Record/save the results (figures and the order of the filter used).
3.   Run your program using step 4.c. Record/save the results (figures and the order of the filter used).
III.  WRITE a short report (in Word or PDF file)1.  Present the figures produced from the above 3 runs. Analyse and explain their differences and the possible reasons for the differences by using plotted figures. Compare the orders of the IIR and FIR filters using plotted figures and give reasons for the differences in the orders. Draw a conclusion (you should justify it) about whether long-term alcohol abuse causes impairments in object recognition and attention, based on the obtained experimental results. [30 marks] 
2.  Based on the obtained experimental results/figures. Suggest a possible method to identify the channels that are most useful to  show the  effects  of long-term alcohol abuse on object recognition and attention impairments. No implementation is required. [10 marks] 
Code quality 
[15  marks] will  be  allocated  to  the  quality  of  your  code  and  commenting,  including  its effectiveness and efficiency.

         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
