---
title: Comparing Two Corpora, Linguistically
authors:
- Richard Soulliere, Beth Mekitiak, Susan Chabot
date: 2015-11-11

layout: default
---


#Comparing Two Corpora, Linguistically

Hello digital humanists, applied linguists, and corpus buffs!  This page documents the process used to create and compare two corpora and displaying the results using a visualization. Click on the links below to find out more about the approach taken, tool(s) used, and steps taken in each section.

<p><dl><dd><a href="#intro">introduction & sources</a></dd>
<dd><a href="#corpart">creating a corpus from an article</a></dd>
<dd><a href="#corplist">creating a corpus from a long list</a></dd>
<dd><a href="#info">dealing with extraneous info & creating a merged corpora</a></dd>
<dd><a href="#vis">creating a visualization</a></dd>
<dd><a href="#conclude">some concluding thoughts</a></dd></dl></p> 

For highly experienced users, do forgive an over-indulgence on explanations and screenshots given that this is designed for any, even people who are complete newbs \(as was the case for ourselves during this trial run\).

<a name="intro"></a>
##Introduction & Sources

When tasked with using a corpora to create a visualization of the data, we did try to use existing corpora available freely online. Finding a compatible, ready-to-go, comma-delinated csv file that could be easy copied and pasted into a tool we selected proved time-consuming. So, another approach was to randomly select a text to do a simple linguistic word count analysis. To make the analysis an analysis and not simply a presentation, it was decided to compare a text against the Academic Word List \(AWL\). What made it more interesting was the text selected \(see biliographic notes below\) was a professor who heads the CTESL program at a university - just to see if professors publish articles that actually contain any items from the AWL!

###Notes
+ Be wary of intellectual property rights, particularly for files you store on github repositories. The article used is not in the public domain, so that file is not included here. The article selected was "Formulaic Language in Acquisition and Production: Implications for Teaching", by Dr. David Wood, published in vol. 20, no. 1 of the TESL Canada Journal in 2002.
+ Copy and paste is, otherwise, amazing.
+ You can check out a tutorial for using github \(including how to fork this repository\) [here](https://github.com/80masters/Github-Tutorial-for-Linguists/blob/master/tutorial_index.md).

<a name="corpart"></a>
##Creating a Corpus from an Article

After selecting the primary text, the next thing we needed was a free word-count generator from which we could create a comma-delinated \(csv\) file. For this, we used [Voyant](http://voyant-tools.org/) together with [SublimeText 3](http://www.sublimetext.com/3) To do so, follow these steps:

1. copy the text \(from the article\) into the box
<p><img src="\images\voyant1.png" alt="Initial Voyant Screen"></p>
2. click on the 'reveal' button
3. assuming that worked, do not freak out with all of the information that comes up on the resultant screen
4. if you do not want simple words such as 'the' or 'as' to be included, set the stop word list by clicking on the gear symbol above the list of words
<p><img src="\images\voyant-stopwords.png" alt="Voyant Stopword Selection"></p>
5. to export, export to csv file
6. a small window will pop up with words, frequencies, and stuff separated by commas so select, copy, and paste into SublimeText
7. If you want more than the top ten words, just below the list of words, click on the right arrow next to 'Page'
<p><img src="\images\voyant-page.png" alt="Voyant Switch Page"></p>
8. repeat steps 6 and 7 until you have the corpora you need

The result from the article cited above can be seen [here](https://github.com/80masters/linguistic-corpora-comparison-visualization-with-voyant-and-raw/blob/master/data-files/Wood-freq-export.md). Please note that if you open this with SublimeText, each word will appear on a new row instead of listed ad nauseum with word wrap.

###Notes:
+ Be sure to repeatedly save your markdown file \(in SublimeText\) so you do not have to start all over again!
+ Do NOT click on the check boxes next to individual words unless you want Voyant to focus on the analysis of only the selected word\(s\).
+ You may find the small pop-up window containing the results to be this weird thing to be swatted like a fly. Don't close it! Those are your results! And be sure to scroll all the way down to the bottom when selecting all of the contents otherwise you'll inadvertently miss out on some of your results.

<a name="corplist"></a>
##Creating a Corpus from a Long List

The AWL is so long, creating a lengthy list proved iritating. Instead, an excel version was found online. The search function in excel could then be used. For a larger corpora from texts, these could be copy and pasted into Excel and then code a macro \(using Visual Basic for Excel \(VBE\)\) to determine whether each word from the text corpora appears on the AWL. However, this was an entirely new endeavor so we did it manually word-by-word.

In all honesty, using Excel helped to create the final merged corpus file, but more on that in the following section.

The AWL file used for this exercise is the \(only\) xlsx file in [this folder](https://github.com/80masters/linguistic-corpora-comparison-visualization-with-voyant-and-raw/tree/master/data-files).

###Notes:
+ The AWL is widely available online. Be on the lookout for variations as they may appear in future depending on the needs of the global English language learning community.

<a name="info"></a>
##Dealing with Extraneous Info & Creating a Merged Corpora

The data that Voyant barfs up contains a lot more than simply words and their frequency in a text. Frankly, the rest was extraneous. The fastest way to get rid of those unwanted "columns" of data was to import the csv file into excel and then simply delete the unwanted columns. A new csv file would then be created by Excel's export function. Also, in applied linguistics, a word is significant if it appears more than four times for every 100,000 words. To reduce the size of the article corpus, given this was a trial run and not a formal analysis, the cut-off was increased to ten appearances.

Next came the issue of merging the text corpus with the AWL. With a two-column csv file \(containing words and their frequencies\) already in Excel, adding another column to indicate whether or not a word was in the AWL proved simple. This was accomplished by adding a comma then either a 1 \(for on the AWL\) or 2 \(for not on the AWL\)\). Since this was only a simple exercise, we did not worry over variations of the same root word, only exact matches.

The resultant csv file can be seen [here](https://github.com/80masters/linguistic-corpora-comparison-visualization-with-voyant-and-raw/blob/master/data-files/Wood-freq-4-cols.csv). It appears in rows here because, well, that's the beauty of a csv file - almost anything can read it as a table. If you open it in SublimeText, the data will appear neatly in rows \(like the file exported from Voyant based on the article cited above\).

<a name="vis"></a>
##Creating a Visualization

The visualization tool for this exercise was [RAW](http://app.raw.densitydesign.org/). As a result of the visualization charts available with RAW and the number of dimensions of our corpus, another dimension was added to our data. This involved adding a fourth column where we could group words according to frequency \(e.g. words appearing 10-14 times were in one group\). Although size is one way of accomplishing this task, adding color made it easier to distinguish words and their frequencies relative to each other. The steps used were as follows:

1. Copy the data from the 4-column csv file into the initial textbox
<p><img src="\images\raw-data.JPG"></p>
2. Select the chart type \(clustered force layout\)
<p><img src="\images\raw-cfl.JPG"></p>
3. Map the dimensions \(i.e. label the dimensions according to the 4 columns\)
<p><img src="\images\raw-map.JPG"></p>
4. Enjoy the results.

The (static) results for this exercise can be seen [here](https://github.com/80masters/linguistic-corpora-comparison-visualization-with-voyant-and-raw/blob/master/images/raw-done.JPG?raw=true).

###Notes:
+ Column headers MUST appear in the first line in step 1!! For our example, it was:
>word, frequency, AWL?, color
+ If you are using Internet Explorer to access this tool, if you make an error or want to make any changes at the mapping stage, you will need to refresh the page \(F5\) and start from scratch. To simplify this, copy your dataset so that you can simply paste it back in. That way, it will only take a few seconds.
+ Various chart types require different dimensions and dimensional relationships regarding your data, so choose wisely.
+ The Clustered Force Layout chart does allow you to pull apart groups \(e.g. words that do or do not appear on the AWL\), but they quickly gravitate back to each other. Fortunately, screenshot tools can provide a static image where groups are separated, but only if your mouse is fast enough! Fortunately, this ability lies well within human capaibilities.
+ You can even copy and paste HTML code of the resulting visualisation for use in an HTML file \(sadly not here on github\)!

<a name="conclude"></a>
##Conclusion
Many of the lessons learned are contained in the notes area at the end of each section \(refer to table of contents at the top of this page\).  However, there are some observations to impart.

First and foremost, it was amazing how fast corpora can be created using these tools. From the moment the task was accepted to the moment the visualization based on the merged corpora was finalized, only two hours had passed - including the learning curve as this was our first attempt at such a task and our first exposure to any of these tools \(MS Excel and SublimeText aside\). That said, these tools seemed geared for smaller corpora as we initially tried the entire works of William Shakespeare, but gave up due to impatience \(or perhaps a lack of RAM\). Likewise for the visualization tool, which seems to effectively cap out around 20 to 30 items.

Second, creating a comma-delinated list proved faster than selecting a random corpora online. They do exist, but compatibility proved to be an issue. Fortunately, the files created for this trial run were saved in markdown as well as one Excel file, which makes it easy to use in other instances. As mentioned earlier, comparing two lists of words all the time can be tedious. However, in MS Excel, a macro could easily be coded in VBE to generate this almost instantly any time you want to do that.

<p><a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-sa/4.0/80x15.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/">Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License</a>.</p>