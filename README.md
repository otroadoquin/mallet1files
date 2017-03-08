# mallet1files
Files and readme for workshop

<H1>Welcome to the Topic Modelling - Mallet Workshop</H1>  

**1.** In order to get started please move the Mallet ... directory from ... to the Desktop.

2) Next, download the found data set that we will be using for the workshop from this page (https://drive.google.com/open?id=0BxwCuF-N-3FpLWVEVkxmM0JTWVU), drag and drop into the Mallet directory on the Desktop and unzip directly into it.

3) As we have seen, Mallet is a commandline tool that requires the use of a terminal emulator. For the purposes of this workshop we will be using Jupyter notebooks because it allows us to easily save our work into a file that we can reference back to and because it's cooler than the built in commandline tools available natively on the big operating systems.

4) Jupyter Notebooks is already installed on the computers, so in order to access it simply open the Terminal application on your computer by selecting the Finder (this will open your a dialog box), select Applications from the right hand menu, scrolling down until you reach the Utilities folder, within this folder you'll find the Terminal application.

5) Once you have opened the Terminal application all you need to type is 'jupyter notebook'. 

6) Jupyter Notebooks will open a page on the browser that should look like the one you are seeing on the projected screen.

7) On the right hand side of the page you will see an <b>'Upload'</b> and a <b>'New'</b> button. Select <b>'New'</b> and from the drop down menu select <b>'Terminal'</b>. This should open a terminal window with the promp:

`bash-3.2$`

8) Now we will navigate to the Mallet folder where we unzipped the files by typing:

`bash-3.2$ cd ...`

9) We can access the Mallet application only from this folder and we do so by invoking the program via 'bin/mallet':

`bash-3.2$ bin/mallet -help`

This will give you a list of all the commands available within the program. We will be working with two in particular:
'import-dir' and 'train-topics'. The first will import all files within a directory or folder that we tell it to and the second will generate the groups of words that make up the topic. There are additional options and syntax to these commands but it's important to first understand that these two commands work very similar to an 'Open' and 'Process'  options similar to a word processor in which you would click as needed. The difference here is that you are behind the scenes telling the program what to do instead of simply clicking the preconfigured buttons.

10) To get started with the actual Mallet topic modelling the first thing that we need to do is import the data into Mallet and in a format that it can understand. Therefore we would first write (we recommend copy and pasting the directory where the txt file are to avoid errors from typing it out, both are supported):

`bash-3.2$ bin/mallet import-dir --input ... --output narrative.mallet --keep-sequence --remove-stopwords`

There are 5 parts that we haven't discussed in this first operation. 
`--input` tells the program where the files that you want to import are located.
`--output` is where to send it as you can imagine but 
It also needs the name of the file and the extension '.mallet' in order to work with the program. The name of the file doesn't matter but the <b>.mallet</b> is mandatory. (Think of .doc for word files or .pdf for PDF files). 
`--keep-sequence` maintains the order of the files since remember we are importing a folder and not just individual files and 
`--remove-stopwords` eliminates a pre-defined list of commonly repeated words from English language (this list can be modified or added to via a secondary list that you create).  

11) The program runs this operation rather quickly and you will now if it's finished when you see the command line promt again. You can check if the file was created by typing the following and looking for the file that you named >narrative.mallet:

`bash-3.2$ ls`

12) With the texts imported and converted into a format that Mallet can work with, we can now ask it to train the topics or the list of word groups that it selects as related according to a topic. Enter the code below and wait before pressing enter. 

`bash-3.2$ bin/mallet train-topics --input ...narratives.mallet --num-topics 20 --optimize-interval 20 --output-state topic-state.gz --output-topic-keys narratives_keys.txt --output-doc-topics narratives_compostion.txt`

The first thing you should notice is that the `train-topics` command works very similar to the `import-dir`, (i.e. we have to tell mallet that a file goes in `--input` and then which file by telling it where it is. The two following options are not as straightforward. `--num-topics #` is the total amount of topics that will be generated per file. The `--optimize-interval` allows us to set the amount of time that a particular algorithm will run in order to calculate the weight of a topic within a file and as a whole. The last three are different versions of output: `--output-state ...gz` is a complete list of all words and is useful for debugging, `--output-topic-keys ...txt` is a list of all topics with their weight, and `--output-doc-topics ...txt` is a list of the weight and topic key number (corresponding to the previous document) by file. All three are easier to view within a specific program which we will get into after.  

13) Now press enter. (inference questions)

14) Please open the narratives_key.txt and narratives_composition.txt files in Excel. And you're done with the easy part! 

