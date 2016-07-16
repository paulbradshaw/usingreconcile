# Using reconcile

[Reconcile](https://github.com/maxharlow/reconcile) is a way of grabbing company details from Companies House. The [GitHub repo readme](https://github.com/maxharlow/reconcile) explains how to install it, and some commands. **Once you've installed it**, this is a step by step example of how to use it:

## Step 1: Create a CSV with the base data you want to add to

First you need to create a CSV file with a list of the company numbers (or other data) that you want to grab more information on. There's an [example in this repo](https://github.com/paulbradshaw/usingreconcile/blob/master/testreconcile.csv) (click 'Raw' to see the raw file and save it if you need to).

I'm going to be using the `company-numbers-to-company-officer-names` command, so the CSV file needs one column named *companyNumber* and another named *companyJurisdiction*.

Fill the CSV with a few company numbers you definitely know exist in the UK (use Beta.Companieshouse or OpenCorporates to find them), and then next to each put `gb` for the jurisdiction. This is the code that OpenCorporates uses for UK companies.

Save it somewhere you can find easily on your computer.

## Step 2: In Terminal go to the location of that file

Open Terminal (these instructions assume you're on a Mac for now) and type `pwd`, then press Enter. This command (it means print working directory) will tell you what directory Terminal is currently working in (for example */Users/Paul/Desktop*).

You need to be in the same place as that CSV. If you're not, you can move there by using the `cd` (change directory) command.

For example if I'm in */Users/Paul/Desktop* and want to move to a folder on the Desktop called 'testing', I can type the command `cd testing`.

If you are not sure where you are, try typing `ls`: this command will list all the folders in the current directory. You can then type `cd` followed by the name of one of those directories to move into it.

Another useful command is `cd /` - this will take you right to the *root* directory on your computer: the root directory has folders like Applications, System and Users. You will generally need to go into users (`cd Users`) and then your username (`cd paul`) to get to familiar territory. A quicker way of getting to the home folder of your own account (in this example, **/Users/paul**), however, is `cd ~`

Once you're in the same location as the CSV file, you can run Reconcile.

## Step 3: Run Reconcile

In Terminal, type `reconcile` followed by the name of the command you want to use, and then the name of the CSV file, like so:

`reconcile company-numbers-to-company-officer-names testreconcile.csv`

The example above is using the *command* `company-numbers-to-company-officer-names` and the file we created is called `testreconcile.csv`. 

Your file might be called something different, and you might want to try different commands outlined in the [reconcile repo](https://github.com/maxharlow/reconcile)

You should see the results of that command running using the information in that CSV file: a series of company numbers followed by a comma, and then details of officers.

If you get `ENOENT: no such file or directory, open 'testreconcile.csv'` then you've either typed the filename wrong, or you're not in the same directory. Check the instructions above again.

Once it's worked, great - but how do you save that into a file you can use?

## Step 4: Saving the results

All we need to do is add `> whateveryouwanttocallit.csv` to the end of what we just wrote (and yes, you can call it anything). The full line looks like this:

`reconcile company-numbers-to-company-officer-names testreconcile.csv`
