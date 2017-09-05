# Ignore Commands in History

My friend Andrew is working on a system to store all of your life's data, and one of the things I find most compelling is its ability to give me a searchable bash history across all time and space.

To that end, I want to be able to type passwords and secrets without it being saved.

In order to have commands prefixed with a space ignored by bash history, in `.bashrc` put:

```bash
export HISTCONTROL=ignorespace
```

Then

```bash
 this is not saved
 
this is saved
```


