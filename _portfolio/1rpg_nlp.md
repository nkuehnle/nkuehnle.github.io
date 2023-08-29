---
title: "Labeling Fan-Generated Roleplaying Game (RPG) Content: An NLP Task"
excerpt: "RoBERTA-based sequence classifier modeling on a novel natural language dataset achieving a macro-averaged F1 score of 0.88 with an AUC/ROC of .99.<br/>The full repository with notebooks [can be found on my GitHub repo](https:/github.com/nkuehnle/rpg_nlp).<br/><img src='https://raw.githubusercontent.com/nkuehnle/rpg_nlp/main/eda/TF-IDF_Doc_EDA_DIR_Submission_Flair_UMAP.png' height='66%' width='66%'>"
collection: portfolio
permalink: rpg_nlp
---

# Overview
Briefly, I collected several thousand links to fan generated role playing game content designed for Dungeons and Dragons 5th edition and its Open Gaming License derivatives from the /r/UnearthedAcana and /r/DnDHomebrew subreddits, including post information such as user voting scores and post flairs (user-specified tag keywords).

For simplicity’s sake, I targeted posts with links to the following domains: homebrewery.naturalcrit.com and gmbinder.com as these websites provide a useful markdownstyle notation for creating this type of content that makes collecting the relevant text convenient (not requiring any optical character recognition, etc). These texts will were used to generate the features for learning while the actual task was to predict the user-provided submission flair, which on /r/UnearthedArcana is both a) mandatory and b) meaningfully related to the kind of types of content that occur in the game rules.

Examples of raw and rendered content taken from the recently-posted public content of gmbinder.com can be found below:

## Example of Raw Markdown/Source Text
```
# Bodysmither Specialist
There are works that draw fury from the nobility, those that revolt temples, and
others that drive academics crazy. The art of bodysmithing outrages all of them. It
is not an ungrateful labor, however. Not by a long shot. The bodysmither provides
for those in need of accessibility and the mad overachievers alike. No bodysmither
works the same, but no matter if their craft takes the form of prosthetic machines,
bio-enhancements or magic-imbued primal elements, the bodysmither takes fulfillment
on the perfection of bodies and the amazing feats anyone with enough drive (and
bodily humours) can accomplish.
### Tools of Physiology
_3rd-level Bodysmither feature_ <br><br>
You gain proficiency with the Medicine skill. If you already have this proficiency,
you gain proficiency with one other skill or tool of your choice. You know how to
create, repair and apply prosthetics using the Medicine skill or tool of relevance.
<br>
### Bodysmither Spells
_3rd-level Bodysmither feature_ <br><br>
You always have certain spells prepared after you reach particular levels in this
class, as shown in the Bodysmither Spells table. These spells count as artificer
spells for you, but they don’t count against the number of artificer spells you
prepare. <br>
##### **Bodysmither Spells** <br><br>
| Artificer Level | Spell |
|:---:|:-----------:|
| 3rd | _fog cloud, magic missile_ |
| 5th | _barkskin, shatter_ |
| 9th | _animate dead, call lightning_ |
| 13th | _greater invisibility, locate creature_ |
| 17th | _modify memory, Rary's telephatic bond_ |
### Maintenance Hobbyist
_3rd-level Bodysmither feature_ <br><br>
You know how to create, apply and maintain protheses, and it’s something you delight
off during your free time! You may work on a number of prosthetics and Augmentations
equal to double your proficiency modifier while taking short or long rests. For the
purposes of resting, maintenance work is considered a light activity for you, and
you don’t need to make skill checks to maintain a prosthetic. You can use a
maintained prosthetic on yourself as a spellcasting focus for your artificer spells,
and can also apply your Magic Tinkering features to them. <br>
You can create Disposable or Permanent prosthetics that simulate natural movement. A
Disposable prosthetic can be created during a Short Rest expending 50gp of materials
at hand. A disposable prosthetic breaks completely at the beginning of the user’s
next long rest. You may then recreate it, expending more 25gp in materials. To build
a Permanent prosthetic you must expend 500gp in materials during a Long Rest. You
can create only one prosthetic per rest. <br><br>
> ##### Adaptation
> Despite the bodysmither work being (mostly) carefully done to avoid complications,
the process of adaptation to new prosthetic limbs is still tough. The user takes 1
point of exhaustion per new prosthetic at application, and at the end of each day,
for 1d6 days. The user may also experience disadvantage on activities that require
effort or finesse for 1d4 days from implementation.
<br>
Additionally, whenever a character receives a prosthetic addition, roll 1d6, or
choose, between the following recurring side-effects: <br><br>
| d6 | Loot |
|:---:|:-----------:|
| 1 | The user loses sensation of the prosthetic area |
| 2 | Pain is heightened on the prosthetic area |
| 3 | Weather may cause the prosthetic to creak or jam |
| 4 | The user might need to concentrate to control the prosthetic’s strength |
| 5 | The area of the prosthetic may get infected from time to time |
| 6 | The prosthetic may sometimes move by its own |
<br>
<img src='https://64.media.tumblr.com/9bffaa82bee273aae06e22581485cb6b/
7721d6bf11dd52b3-bb/s1280x1920/27452c589f541c8403401ab03fbc67111b802513.png'
class='image-right-bottom' width='273'>
\pagebreak
```

## Example of Rendered View
<img src='https://nkuehnle.github.io/images/gmbinder_example.jpg' height='150%' width='150%'>

# Performance
RoBERTA-based sequence classifier modeling on a novel natural language dataset achieving a macro-averaged F1 score of 0.88 with an AUC/ROC of .99.

<img src='https://raw.githubusercontent.com/nkuehnle/rpg_nlp/main/eda/TF-IDF_Doc_EDA_DIR_Submission_Flair_UMAP.png' height='80%' width='80%'>

## Per-Class Performance

|           | Training Recall | Testing Recall | Testing Precision | Testing F1-Score |
|-----------|-----------------|----------------|-------------------|------------------|
| Class     | 0.95            | 0.90           | 0.93              | 0.91             |
| Feat      | 0.86            | 0.72           | 0.84              | 0.78             |
| Item      | 1.00            | 0.93           | 0.90              | 0.92             |
| Mechanic  | 0.99            | 0.80           | 0.61              | 0.69             |
| Monster   | 0.98            | 0.98           | 0.97              | 0.97             |
| Race      | 0.97            | 0.88           | 0.91              | 0.90             |
| Spell     | 0.96            | 0.96           | 0.98              | 0.97             |
| Subclass  | 0.96            | 0.97           | 0.97              | 0.97             |

Overall, it seems like Feats and Mechanics are holding back performance quite a bit. Feats are likely to have a lot of conceptual overlap with classes and subclasses (i.e. a subclass is really just a collection of "subclass features" which read very similarly to feats). Mechanics are wide and diverse, so learning them may prove a difficult task. While there is some evidence of overitting, the degree of overfitting seems particularly high for mechanics, which makes sense since mechanics are probably one of the most diverse elements in the dataset, sometimes devolving into entire new systems/rules of play that resemble a different game altogether. Beyond that, the Race and Feat labels may also be overfit. For the Race flair/label category, overall testing performance is at least generaly quite impeccable.

# Access
The full repository with notebooks [can be found on my GitHub repo](https:/github.com/nkuehnle/rpg_nlp).

# Data Availability
Data (raw inputs and trained models) are [available on Google Drive](https://drive.google.com/drive/folders/1ORpfjjJTjaTWUFI6DquHMQhqIT8v9k2B).
