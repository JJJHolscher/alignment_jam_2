Repository with notebooks for the [interpretability hackaton](https://itch.io/jam/interpretability) from Apart.

# Abstract of our research and findings

We investigate a recent model editing technique for large language models called Rank-One Model Editing ([ROME](https://rome.baulab.info/)). ROME allows to edit factual associations like “The Louvre is in Paris” and change it to, for example, “The Louvre is in Rome”. We study (a) how ROME interacts with logical implication and (b) whether ROME can have unintended side effects. 

Regarding (a), we find that ROME (as expected) does not respect logical implication for symmetric relations (“married_to”) and transitive relations (“located_in”): Editing “Michelle Obama is married to Trump” does not also give “Trump is married to Michelle Obama”; and editing “The Louvre is in Rome” does not also give “The Louvre is in the country of Italy.”

Regarding (b), we find that ROME has a severe problem of “loud facts”. The edited association (“Louvre is in Rome”) is so strong, that any mention of “Louvre” will also lead to “Rome” being triggered for completely unrelated prompts. For example, “Louvre is cool. Barack Obama is from” will be completed with “Rome”.  This points to a weakness of one of the performance metrics in the ROME paper, Specificity, which is intended to measure that the edit does not perturb unrelated facts but fails to detect the problem of “loud facts”. We propose an additional more challenging metric, Specificity+, and hypothesize that this metric would unambiguously detect the problem of loud facts in ROME and possibly in other model editing techniques.

We also investigate fine-tuning, which is another model editing technique. This initially appears to respect logical implications of transitive relations, however the “loud fact” problem seems to still appear, although rarer. More investigation is needed.
