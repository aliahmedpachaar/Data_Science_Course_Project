Project Progress Report: Fixes and Extra Experiments

Introduction and Goal

On Day 4 I checked the notebooks from Day 1-3 and found some problems that made results look better than they are. I fixed them, rerun everything and did the extra experiments.

Phase 1: Fixes

- Data leakage: TF-IDF was fitted on all books before the split. Now it is inside a Pipeline, so it learns only from training data.
- Model was picked by looking at the test score. Now it is picked with cross-validation and test set is used only once at the end.
- Grid search used accuracy, but classes are imbalanced (63% fiction). Now we use macro-F1.
- Title features are now scaled, they were much bigger than TF-IDF values.
- Text cleaning glued words together ("midnightwith"). Fixed.
- Scraper encoding bug ("Â£") fixed with UTF-8, and all 1000 books rescraped.
- "Historical" category has only 2 novels, so it is Fiction now.

Phase 2: New Results

781 books (496 Fiction, 285 Non-Fiction). Best model is LinearSVC with cross-validation macro-F1 0.864. On the test set it gets 89.2% accuracy and macro-F1 0.881. Almost same as before (89.8%) but now the number is honest. After scaling, the colon feature is not the strongest predictor anymore.

Phase 3: Images and Subset

- Raw HOG still makes the model much worse (0.610). HOG with PCA gives a very small gain (0.878), too small to trust, so we kept text only.
- Using only the site's Fiction and Nonfiction categories (175 books) gives macro-F1 0.847, but data is too small.

Phase 4: Error Analysis

Hardest categories are Sports and Games, Travel, Humor and Music. Many errors are wrong labels on the website, for example 3 of 5 Sports and Games books are romance novels.

Current Status and Next Steps

Coding is done. Figures for the report are in the figures folder. Next: final report.
