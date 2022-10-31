# Lab Report 1 (Week 1)
## Interesting Command-line Option Interactions

This report will focus on the command grep and will show some interesting command line options that can be used with the grep command

### Part 1 - Grep
The command grep is used to mostly look through directories. The command is used either to search through output that is piped to it or search through the current working directory.

### Part 1 - -v
 The command -v is an interesting command because it allows us to invert the match that we search. This is useful because sometimes it might be easier to group up the things you don't want outputted rather than the things you do want outputted and if you're able to group up the things you do want in some way with grep, then this command will allow you to output what you do want outputted as well.

 Examples of this command will shown with the technical folder from week 4:

 If we wanted to only show the folders in technical that dont contain 'me' in their title then we could use the command:


    (base) michael@Michaels-MacBook-Air technical % ls | grep -v me
    911report
    plos

Since we piped the contents of the working directory to grep through the use of ls, we showed that the directory technical only has the directories '911report' and 'plos' in it that don't contain 'me' in their title and this is shown true if we just show the output of ls as well.

    (base) michael@Michaels-MacBook-Air technical % ls
    911report	biomed		government	plos

If we wanted to get all the chapters of the 911 report except for chapter 13 since it is in 5 parts you could use the grep -v  command like this:
    (base) michael@Michaels-MacBook-Air 911report % ls | grep -v 13
    chapter-1.txt
    chapter-10.txt
    chapter-11.txt
    chapter-12.txt
    hapter-2.txt
    chapter-3.txt
    chapter-5.txt
    chapter-6.txt
    chapter-7.txt
    chapter-8.txt
    chapter-9.txt
    preface.txt 

And if we wanted to get the files in the folder /government/Env_Prot_Agen that aren't tech related we would use the command like this:

    (base) michael@Michaels-MacBook-Air Env_prot_agen % ls | grep -v tech          
    1-3_meth_901.txt
    atx1-6.txt
    bill.txt
    ctf1-6.txt
    ctf7-10.txt
    ctm4-10.txt
    final.txt
    jeffordslieberm.txt
    multi102902.txt
    nov1.txt
    ro_clear_skies_book.txt
    section-by-section_summary.txt

## Part 2 - character classes
character classes in grep allow us to have multiple different characters for a spot, for example b[aou]y would match bay, boy, and buy.

In the 911report directory if we wanted to show all the chapters before 10 we could use the grep command:

    (base) michael@Michaels-MacBook-Air 911report % ls | grep -E "chapter-[0123456789].txt"
    chapter-1.txt
    chapter-2.txt
    chapter-3.txt
    chapter-5.txt
    chapter-6.txt
    chapter-7.txt
    chapter-8.txt
    chapter-9.txt

In the directory /government/Env_Prot_Agen then we could us the grep command to search for all the ctf and ctm files except for the one the file ctf1-6.txt:

    (base) michael@Michaels-MacBook-Air Env_prot_agen % ls | grep -E "ct[fm][^1]"
    ctf7-10.txt
    ctm4-10.txt

This command also showed the use of multiple character classes in the same command allowing for even more ability to control what you're searching for with the grep command.

In the Biomed directory if we wanted all the files with 1471-2091 but we didnt want the ones from february. We could use the grep command:

    (base) michael@Michaels-MacBook-Air biomed % ls | grep -E "1471-2091-[^2]"
    1471-2091-3-13.txt
    1471-2091-3-14.txt
    1471-2091-3-15.txt
    1471-2091-3-16.txt
    1471-2091-3-17.txt
    1471-2091-3-18.txt
    1471-2091-3-22.txt
    1471-2091-3-23.txt
    1471-2091-3-30.txt
    1471-2091-3-31.txt
    1471-2091-3-4.txt
    1471-2091-3-8.txt
    1471-2091-4-1.txt
    1471-2091-4-5.txt

In this case the carat character acts as a way to negate what is in the charactrer class already. This means any file with a 2 in that character slot will not show up with the grep command.


## Part 3 - -c
Grep allows us to get the count of number of items that our grep will hold too. This can be useful for counting files if you don't know the exact count.

For example if we want to know the number of rr files we have in the biomed file we can use the grep command:

    (base) michael@Michaels-MacBook-Air biomed % ls | grep -c rr     
    9

If we want to know the number of Office of the Genreal Counsel files we have in the government/Gen_Accounting_Office file we can use the grep command:
    (base) michael@Michaels-MacBook-Air gen_account_office % ls | grep -c og      
    57  

And if we wanted to know the number files with 1471-2091 but not including the ones from March we would use the grep command:
    (base) michael@Michaels-MacBook-Air biomed % ls | grep -Ec "1471-2091-[^3]"
    10
This shows us an example of a use of both regular expressions and the -c command.