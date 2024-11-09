Presents 2 second sinusoidal grating and 3 second gray screen for user-define amount of trials
# Summary

Presenting sinusoidal visual gratings between isoluminescent grey screens while recording locomotion via wheel encoder.



## Important Features



### System Argument input from a Parent Process

This experiment contains a STDINPUT routine built to receive command line arguments from a Parent process when launching this experiment as a Subprocess using the built-in python `subprocess` module. This code is meant to circumvent the usual launch of a PsychoPy experiment, forgoing manual entry of subject information into a popup dialog box.



This block allows standard input system arguments to define:

- BIDS format information for file saving 

- number of Trials calculated from a Parent process



### Custom file saving behavior

Enabled by input from `sys.arg`, this can be customized in the CustomSaving routine's custom codeblock `save_encoder_data`



We simple hijack PsychoPy's `_thisDir` attribute to save data to the same `data` folder with a filepath relative to the directory the script is located in at runtime.



### Threaded Rotary Encoder Recording

Custom code launches a python `threading` thread for reading serial output from an arduino-controlled encoder. The thread `deque` is sampled (FIFO) from the main experimental loop at the screen refresh rate (eg. 60Hz).



Raw encoder `clicks` are decoded and processed on-the-fly (this is customizable) and data is stored as a `/dataframe.csv` at the end of the experiment.



### Custom Start triggers

The experiment builder file contains custom routines built for NIDAQs using the `nidaqmx.Task` python module. These routines allow for signal trigger input to start the experiment or signal trigger output to trigger external systems upon the start of the experiment. 



Otherwise, the spacebar is used to start the experiment.