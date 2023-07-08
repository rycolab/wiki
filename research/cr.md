# Camera Ready Guidelines
### Ryan Cotterell and Isabelle Augenstein

So, you’re the proud new owner of an accepted paper at a top computer science conference, eh? Here are the five steps to make publishing the final version a painless camera ready process! Why is this process called camera ready? Read about it [here](https://en.wikipedia.org/wiki/Camera-ready): etymology is awesome!

## Step 1: Start with the Basics
* Take the paper and turn it into camera ready mode. With the .sty file used by the ACL community, you typically do this by uncommenting the line `\aclfinalcopy`. 
* Add the author list, following the [Rycolab style guide’s specifications](./style.md).
* Make sure you are following other aspects of the style guide, e.g. use of cref.
* Make sure your paper has an “Ethical Concerns” section. If it did not during submission, please add it. It is totally fine if you foresee no ethical concerns with your work. Even if this is the case, you should still declare this. 
    * It’s better to declare that you foresee no ethical concerns than trying to make up ethical concerns that you don’t actually foresee or agree with because you feel peer-pressured into doing so. You can also consult with someone you trust on this point if you are not sure.

## Step 2: Address the Reviewers’ Concerns
* Copy the final reviews into a Google doc (see [here](./rebuttal.md)) and send it to all your co-authors: 
    * Create a list out of the concerns you plan to address;
    * I start with the simple concerns, e.g., typos and missing indices in formulae, just to get the ball rolling;
    * Then, move into the more substantive changes: For instance, argumentation or clarification rewrites. 
* If you make a substantive change, you must leave a todo note tagging your other co-authors, so everyone knows to check that section in more detail. Our goal is not only to fix errors, but also not to introduce new ones!

## Step 3: Proofread for Language Typos
* Run [aspell](https://en.wikipedia.org/wiki/GNU_Aspell) or another spell-checker a few times and make changes.
* Make sure you proofread for typos. Finding typos is hard. We have a cognitive bias to not see typos in passages we wrote ourselves because we already knew what we wanted to say.
    * Some typo-catching tips:	
        * Print out the paper and read it with a pen, pencil or highlighter in hand;
        * Try reading bits of the paper out loud;
        * Swap with a labmate and check each other’s papers.
* A note for non-native speakers of Our ~~[Magnificent Bastard Tongue](https://www.amazon.co.uk/Our-Magnificent-Bastard-Tongue-History/dp/1592404944)~~ English
    * Don’t worry! The level of English used in scientific publications is relatively low, so you don’t have to be [Joseph Conrad](https://en.wikipedia.org/wiki/Joseph_Conrad) to write great *ACL papers. (Fun fact: Joseph Conrad, one of the greatest stylists in the English language, didn’t learn English till his 20s!)
    * In fact, I tend to think non-native English speakers write better works of science because they don’t muck about with all that [prescriptivist poppycock](https://languagelog.ldc.upenn.edu/nll/?cat=5) hammered into native speakers’ heads as younglings. (They also refrain from using ridiculous terms like perspectivist poppycock...)
    * That being said, if you have questions about English grammar or style, please ask in our Zulip chat. Many members of our lab are native speakers of English and can help out at a moment’s notice. 

<span style="color:red"> Note: Ryan is ok with the paper being arXiv-ed at this point. However, it should be updated after step 5. </span>

## Step 4: Proofread for Mathematical Typos
* Math typos are even harder to spot than language typos. There is even more cognitive bias! So, we have to be extra careful. I’ll describe the procedure I am adopting here. 
* Every formula and mathematical proof needs to be signed off by at least two people, at least one of whom is me. Ideally, every co-author checks every bit of the paper in math mode.
* To ensure this check happens, create a colored math macro that highlights the mathematical formulae that are to be checked. You could create, for instance, \newcommand{\mathcheck}[1]{{\color{red} #1}} and place all formulae to be checked in that environment. This will render them as bright red in the pdf; the rule is you can’t turn off your own macros!
* It is also helpful to have technically trained colleagues look over the mathematical bits. There are always many volunteers for this: Who doesn’t like to dig into some cool math? 

## Step 5: Update the References
* Check if there are any missing references, e.g. papers published since your paper was submitted. Also, it is often common to omit self-citations that would otherwise deanonymize the work during peer review; make sure you put those back in so the work is contextualized in the broader mission of the lab.
* Check if any preprints are now published somewhere, and replace the .bib entries for those. You can e.g. use https://github.com/google-research/arxiv-latex-cleaner for this.
* Go over the reference list one last time and make sure umlauts are rendered correctly, papers and venue titles are capitalized as they should be, and there are no other errors.
* Make sure you are citing people by their proper name. See https://2021.naacl.org/blog/name-change-procedure/. There are tools that help with this https://github.com/yuchenlin/rebiber. 
* Make sure that there are no duplicate entries in the bibliography, these can often creep in when you are collaborating with a number of people.

## Step 6: Accessibility
* In order to make sure our work is accessible on a [screen reader](https://en.wikipedia.org/wiki/Screen_reader), we want to make sure all images have [alt text](https://authors.acm.org/journals/how-to-write-alt-text-and-why). See the following tex overflow post https://tex.stackexchange.com/questions/458906/making-accessible-graphs-in-latex, which suggests the tagpdf package. Please let me know if there is a better option. 
* Also, all videos presenting the work must also have high-quality captions. We can pay about a dollar a minute for this at https://www.rev.com/caption, so please ask me for reimbursement. 

## Step 7: Reproducibility
Make the codebase for the empirical portion of the paper publicly available. Add a reference link in the paper.
Research code is notorious for being terribly documented and having poor style; let’s make the effort to break that norm! All paper codebases should have the following:
* List of dependencies
* A nicely-written README that includes:
* A set of “quick-start” commands that can get the user up and running (e.g., to reproduce a specific set of experimental results)
Ideally, a more detailed description of the exact commands needed to reproduce all experimental results
* Links to paper/bibtex 

## Step 8: Add an Acknowledgements Section
* At the minimum, make sure to acknowledge your funding source(s). 
* If there’s anyone who helped you in preparing the paper, but is not a co-author, you can thank them here as well. You should be generous; an acknowledgement costs nothing. 

## Step 9: Make Sure Ryan Knows about the Deadline and Submit
* All authors have to sign off on the final version. All authors should also generally do an intense proofread of the paper. It is the more senior authors’ responsibility to ensure the correctness of the paper, a trick picked up from Hanna Wallach. We should all strive to match her rigor. 
* The most senior authors also have a lot of stuff on their plate. Thus, you’re going to have to make sure that they don’t forget about the deadline. Ask Tiago for the best Ryan-pestering tricks!
* There are a very small number of acceptable Ryan substitutes, i.e. people who I trust to ensure a high-quality document. Thus, if there is an additional senior researcher on the paper, make sure they know about the deadline as well!

## Step 10: Submit the Final Version!
* Upload the final paper to softconf (or the equivalent conference manager)
* Before submitting to *ACL venues, run the paper through the [formatting checker](https://github.com/acl-org/aclpubcheck). It only takes a minute and catches basic margin/formatting errors that you will otherwise get an angry email about from the pub chairs 😶
* At this point, if you have already uploaded the paper to arXiv, it should be reuploaded to ensure that it matches the final journal/proceedings version.

## Step 11: Prepare the Website Information
* Make sure the metadata for your paper is updated in the [Rycolab paper Google sheet](https://docs.google.com/spreadsheets/d/1bkwiXM3pRmWsa1NHqcKvJLsQy19HUaMz6LJ-xsjIDGM/edit?usp=sharing).
* Select a first-page picture that is to be displayed on the website. This picture should be uploaded to https://drive.google.com/drive/folders/111SdX1hoDtEcaR5aMMdbCld_l0SYVwgT?usp=sharing. 
* Ping the current website publications czar (currently Ran) to update the website so it displays on the “Recent Publication” bit of the website. 

## Step 12: Promote your Paper on Social Media
* Make sure your paper is uploaded on arXiv. Once your paper is pushed to arXiv, you should share the paper password with _**all**_ your co-authors. This is best achieved by forwarding the email you received from arXiv.
* If you so choose and wish to Tweet about your paper, draft a Tweet in a Google doc in this folder https://drive.google.com/drive/folders/14MUUJ3xdzB4LC1lIgBAbbulh8peP-M2b?usp=sharing. You can inspect previous lab Tweets for inspiration.
* Make sure _**all**_ your co-authors proof-read the Tweet to ensure the Twitter mob doesn’t come after you. (Just ask Jun–it’s an unpleasant experience.)
* Hit Tweet! (Or some other social media send button.)

## Step 13: After Publication
* Even if you’ve followed these steps [down to a T](https://writingexplained.org/idiom-dictionary/down-to-a-t), it is still possible that you’ve missed some errors. That’s ok! The important thing is to not be embarrassed/shy about making corrections.  I add errata to my papers quite a bit when I find mistakes; it’s proper scientific practice. Here is a [good example](https://arxiv.org/pdf/1808.10024.pdf) of how I do post-publication errata.
* Any corrections need to be propagated to both the journal/proceedings version and to the arXiv version. Ideally, headers and a list of errata corrections should be added, as in [here](https://arxiv.org/pdf/1808.10024.pdf). To make corrections to the arXiv version, you simply need to issue a replacement. For journal/proceeding versions, it depends on the venue. The procedure for the ACL anthology is quite simple; see [here](https://www.aclweb.org/anthology/info/corrections/).
