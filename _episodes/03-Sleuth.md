---
title: "Using Sleuth"
teaching: 15
exercises: 0
questions:
objectives:
- "Introduction to Sleuth"
keypoints:
---

# Getting Started with Sleuth

The first step will be to load the files we need.  We will need to tell the computer where to find
each replicate kallisto output and the relationship table.

```
#----------|to load files|----------#

# Different runs
sample_id <- dir(file.path("..", "files"))

# each replicate loaded
kal_dirs <- sapply(sample_id, function(id)
  file.path(main_work_dir, "files", id))
kal_dirs

# relationship table
s2c <- read.table(file.path(main_work_dir, "hiseq_info.txt"),
                  header = T, stringsAsFactors = F)
s2c
```

To help sleuth understand what we wish to do, we will need to trim the relationship table.

```
#### NOTE TO STUDENTS:
#### Recall that in the below case, :: means use the function 'select'
#### in the library 'dplyr'
s2c <- dplyr::select(s2c, sample = run_accession, condition)
s2c

s2c <- dplyr::mutate(s2c, path = kal_dirs)
s2c
```

We will now make a sleuth object.  The functions called here come out of the sleuth library we
attached earlier.

```
#----------|making sleuth object (SO)|----------#

so <- sleuth_prep(s2c, ~ condition)

so <- sleuth_fit(so)

so <- sleuth_wt(so, 'conditionscramble')
```

The final step would be to call the R shiny app to help visualize the data.  If you wish to bypass
this, the data can be saved using models(), and manipulated to your preference.

```
# Visualize
sleuth_live(so)

# to save data
models(so)
```

# Understanding sleuth output
