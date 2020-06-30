---
layout: template
title: Running NetLogo on a Condor cluster
sub_title: How do run your simulations efficiently while minimising headaches
---

# Running NetLogo on a Condor cluster


For the dissertation of my Master's in Big Data, I had the pleasure to work with NetLogo to develop an agent-based model, and the satisfaction to use a Condor cluster to speed up the simulation runs and avoid losing the use of my own laptop for days at a time.
However, when I was looking for instructions on how to set up NetLogo to work through Condor, I was sad to find a lack of specific tutorials. So, for the (I guess) other three and a half people that will probably need this in the future, here is a tutorial!

---

## 1. Set up your experiment in BehaviorSpace
If you're unsure how to do this, [NetLogo's own guide](https://ccl.northwestern.edu/netlogo/docs/behaviorspace.html) is the best place to start. To begin with, you're better off designing a **simple "test" experiment** that just runs your model once with a set of base parameters. Call it something easy to remember and save your .nlogo file.

When you're designing the experiment, make sure to add all the reporters you will need: each reporter will have its own column in the resulting .csv file.

## 2. Set up your submission file
If you're reading this, chances are you already know what Condor is and what a submission file is, but are unsure how to set up one for your NetLogo model. NetLogo is **implemented in Java**, which means we don't need to have NetLogo installed on the Condor machines for the model to work - they just require a **an up-to-date Java Virtual Machine**. The submission file will look like this:

### model-submission.sub (suitable for copy-pasting)
```
universe = java
executable = netlogo-6.1.1.jar
arguments = org.nlogo.headless.Main --model model.nlogo --experiment NAME --table -
transfer_input_files = model.nlogo
jar_files = netlogo-6.1.1.jar,args4j-2.0.12.jar,asm-all-5.0.4.jar,autolink-0.6.0.jar,behaviorsearch.jar,commons-codec-1.10.jar,commons-logging-1.1.1.jar,config-1.3.1.jar,flexmark-0.20.0.jar,flexmark-ext-autolink-0.20.0.jar,flexmark-ext-escaped-character-0.20.0.jar,flexmark-ext-typographic-0.20.0.jar,flexmark-formatter-0.20.0.jar,flexmark-util-0.20.0.jar,gluegen-rt-2.3.2.jar,httpclient-4.2.jar,httpcore-4.2.jar,httpmime-4.2.jar,jcommon-1.0.16.jar,jfreechart-1.0.13.jar,jhotdraw-6.0b1.jar,jmf-2.1.1e.jar,jogl-all-2.3.2.jar,json-simple-1.1.1.jar,log4j-1.2.16.jar,macro-compat_2.12-1.1.1.jar,parboiled_2.12-2.1.3.jar,picocontainer-2.13.6.jar,rsyntaxtextarea-2.6.0.jar,scala-library-2.12.8.jar,scala-parser-combinators_2.12-1.0.4.jar,scala-parser-combinators_2.12-1.0.5.jar,shapeless_2.12-2.3.2.jar
should_transfer_files = YES
when_to_transfer_output = ON_EXIT
log = DATE_NAME.log
error = DATE_NAME.err
output = DATE_NAME_$(Process).csv
Queue 10
```

If copy-pasting this, make sure to update the following:

- `transfer_input_files` (required): make sure this parameter reflects **the name of your actual .nlogo file**, which for me here is simply model.nlogo;
- `NAME` (required): this is a placeholder that **you must substitute with the name you gave to your experiment**. In the file above, it's also present as part of the output name, which I think keeps things tidy, but feel free to change that to reflect your own naming convention;
- `DATE` (optional): like above, I find it good practice to include the date you ran your job on in the file name to make sure you don't get confused, but ultimately it's up to you;
- `Queue` (optional): depending on how you decide to run your replicates, you might have to change this (see last section for more info);
- `arguments` (optional): the setup above produces a standard table output which is put in the same directory as the original. If you need to change that, or alter some other parameters, see [this section of the BehaviorSpace guide](https://ccl.northwestern.edu/netlogo/docs/behaviorspace.html#running-from-the-command-line);
- `executable` (optional): as of July 2020, NetLogo version 6.1.1 is the most recent, but if you're from the future, a) wow, I can't believe we actually survived 2020, and b) you might want to check the main executable is still called the same, and that the jar_files list hasn't changed.

The important parts of this submission file are: the $(Process) tail of the output, which **will prevent results being overwritten at each run**, and the **list of .jar files**: these can all be found in the app folder of your NetLogo installation (usually C:\Program Files\NetLogo 6.1.1\app). **Locate them** before moving onto the next step.

## 3. Move the necessary files onto the Condor cluster
Unfortunately I cannot give specific information for this section, as it is going to vary a lot depending on how you're accessing your cluster. For example, the cluster I had access to was provided by my University, so I moved the files onto my student drive using a VPN.

Regardless of how you end up doing it, the files that need to be moved where Condor can access them are:

- The **.nlogo model file**
- The **.sub submission file**
- The **.jar files** from the **NetLogo app folder**

Make sure to put all the files in the same directory with no sub-directories, otherwise Condor will not see them and the job will fail (as far as I know).

## 4. Submit your job and getting results
Once all the files are in place, access the Condor terminal (again, this will depend on the structure and nature of your cluster), and **run the command** `condor_submit model-submission.sub`. If you changed the name of your submission file, make sure the command reflects that.

Once the job has finished (you can check its status with the condor_q command), you will find the output files in the same folder as the input files. Expect **one output file per job queued**, e.g. if the last line of your submission file is Queue 10 , then the resulting files will be `file_0.csv, file_1.csv, ..., file_9.csv` , with the numbering starting at 0.

## IMPORTANT: Running 1 job with 100 repetitions vs. running 100 jobs with 1 repetition

This is probably the most critical decision you will have to make in this process. You will have noticed that BehaviorSpace offers the option of scheduling a specific number of runs for each experiment, called repetitions. Say you want to run your model 100 times to check for variation, you have two main options:

**Option 1 - Schedule 100 repetitions through BehaviorSpace and Queue 1 job on Condor:** this is the **slow but tidy** way of doing things, as each machine in the cluster will only pick up one job, meaning that one machine will have to run the 100 repetitions. Unless you're working from a toaster, this is probably going to take about long as your own computer would have taken, but at least you retain access to it. The positive aspect of choosing this option is that Condor will produce a **single output file**, in which the 100 runs will already be correctly labelled. 

### Example of a single file output (3 runs, 2 steps each)
```
output.csv
run_number    step    rep1    rep2    ...
1             1       value   value   ...
1             2       value   value   ...
2             1       value   value   ...
2             2       value   value   ...
3             1       value   value   ...
3             2       value   value   ...
```

**Option 2 - Schedule 1 repetition through BehaviorSpace and Queue 100 jobs on Condor:** this is the **fast but messy** way of doing things, since (again) each machine in the cluster will pick up one job, resulting in the 100 simulations running parallel to each other, finishing the job a lot quicker than if one machine had to run all the simulations one after the other. The downside of this option is that Condor will produce 100 output files, and each one will mark its run as being run number 1, meaning you will have to do some **extra data processing** to merge the output files and label the rows correctly. 
Example of a multiple file output (again: 3 runs, 2 steps each)

```
output_0.csv
run_number    step    rep1    rep2    ...
1             1       value   value   ...
1             2       value   value   ...
output_1.csv
run_number    step    rep1    rep2    ...
1             1       value   value   ...
1             2       value   value   ...
output_2.csv
run_number    step    rep1    rep2    ...
1             1       value   value   ...
1             2       value   value   ...
```

The same pros and cons apply even if you're running experiments that test different combinations of parameters. Make sure you choose the one that works best for you.

---

I hope this helped! If you have any more questions or comments, feel free to contact me on twitter [@alepoptosis](https://twitter.com/alepoptosis). Special thanks to Dr David Cairns at University of Stirling who helped me make sense of this mess and agreed to proofread this tutorial!

