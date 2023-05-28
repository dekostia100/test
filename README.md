# Hello, World!
## Goodbay, World!
роцукр8 пнрр апроле yw7egtfi iugwutgt79t6y84f87g8ert7 g45ryt689e a8e7;t 835038це 3Ц08Е  086Н Ц3ЕЦ30Щкевцгпа  нувм фвфшв фвп ва

пук
пк
п
кп
к
пк
п
п
к
п
кп
п
к
пк
п
кп

пкп
к
у
р
ер
кр

р
цкр
ер


р
к
рк
рк
ерк
р
ккр
кр

ркр
к
ер
екр
р

рк
рк
р


к
к
н
олшг
д

к
о
к
еко


бу
н

гьлул

уенлелцу
ел
е
л
цуелон
ло
уцен
ц
н
ул
лу
ц
лоено
цкн
олце
но
е

он
е
ко
е
ну
н
о
кнокрк
е
ке
ркур
ке
рк
р
екр
к
ер
кр
кер
ке
рке
рнеоркерорпшзкеор
еееееееееееееее
е







е
е

пркеркеркеркр
керкер






керк
р
ер
р
р
р
п
рке
ркеркер



глш
жз
dfb

b


5

898
5+9
89 98798
74897

98
8
894
8649849849844




455
5
5

656

64
64
64
54
54
654
64
4
65456
6
5456
4
54
56
456
56
4
4
4
545
5
645
546
4
5456
456
45
45
45456
456
4564
45
45645456

3434dh
54
ht
rt
uk
urts
dg
xg

h
kytkmh fhymkfb fyhkm 
fhykm
 fvyhmk fvmkfvmkmkmkmkmk                          bbbkg
    j jhduifb diufbdiuhvhherb
    b
    
    bf
    bfsdbdsfbfbmfejbdhbnud
    However, at some point, I created a new branch locally called add-calendar-model in case next steps of the app development would go south...

... which is exactly what happened.

However, despite many attempts, I did not manage to get the initial code — i.e. the code from before I created the new branch — from the master branch to my local repository.

So, I decided to manually delete all the files from my local repository and git clone my master branch from GitHub.

This way, I got all my files back, but now, I cannot push any more to the remote repository.

Any time I try to run git push origin add-calendar-model or git push origin master, I get the following error:

fatal: 'origin' does not appear to be a git repository
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
I am not very comfortable with Git and GitHub, as you may have guessed by now, and I have to admit that I have no clue about how to fix this.

Any idea?

gitgithubversion-controlbranch
Share
Improve this question
Follow
asked Aug 27, 2015 at 0:03
Thibaud Clement's user avatar
Thibaud Clement
6,5271010 gold badges5050 silver badges103103 bronze badges
2
I had a similar error, But my problem was I had initialized git in the parent directory of the current folder I was trying it. Just in case if anyone is still facing, can look where the git is initialized and then try again. – 
Himanshu Kriplani
 Apr 17, 2020 at 2:39
Add a comment
17 Answers
Sorted by:

Highest score (default)

321


First, check that your origin is set by running

git remote -v
This should show you all of the push / fetch remotes for the project.

If this returns with no output, skip to last code block.

Verify remote name / address

If this returns showing that you have remotes set, check that the name of the remote matches the remote you are using in your commands.

$git remote -v
myOrigin ssh://git@example.com:1234/myRepo.git (fetch)
myOrigin ssh://git@example.com:1234/myRepo.git (push)

# this will fail because `origin` is not set
$git push origin main

# you need to use
$git push myOrigin main
If you want to rename the remote or change the remote's URL, you'll want to first remove the old remote, and then add the correct one.

Remove the old remote

$git remote remove myOrigin
Add missing remote

You can then add in the proper remote using

$git remote add origin ssh://git@example.com:1234/myRepo.git

# this will now work as expected
$git push origin main
Share
Improve this answer
Follow
edited Nov 4, 2021 at 20:14
Simo Pelle's user avatar
Simo Pelle
14111 silver badge1010 bronze badges
answered Aug 27, 2015 at 0:06
Matt Clark's user avatar
Matt Clark
27.6k1919 gold badges6767 silver badges122122 bronze badges
It worked for me without the ssh:// in front of git@example.com:1234/myRepo.git – 
Carol-Theodor Pelu
 Jul 16, 2018 at 7:05
I was reading this question if you could help with the new repository push error as well? – 
StaticVariable
 Sep 3, 2018 at 7:04
I renamed my remote branch from upstream to origin and it caused the error, after completely deleting the remote reference using git remote remove origin and then adding it again using git remote add origin <url> then it worked fine – 
Uriahs Victor
 Jun 29, 2021 at 18:31
This worked for me, with a slight tweak. git remote -v was showing that my origin was git@bitbucket.org/[repo].git. After removing that origin, I replaced it with just bitbucket.org/[repo].git, and this worked. To clarify, I got rid of the "git@" and just put in the repo URL without a user, prompting it to ask for a user for all push/pull commands (which is what I needed anyway). – 
Bad Programmer
 Aug 3, 2022 at 17:59
Add a comment

31


It works for me.

git remote add origin https://github.com/repo.git
git push origin master
add the repository URL to the origin in the local working directory

Share
Improve this answer
Follow
answered Jul 21, 2020 at 8:22
vinod's user avatar
vinod
52555 silver badges1010 bronze badges
2
When I removed the *.git in the end it worked for me: git remote add origin https://github.com/user/repo – 
Joel Wiklund
 Nov 5, 2022 at 7:12
Add a comment

16


As Matt Clark stated above

However, origin might not be set, so skip the deleting step and simply attempting to add can clear this up.

git remote add origin <"clone">
Where "clone" is simply going into your GitHub repo and copying the "HTTPS clone URL" and pasting into GitBash

Share
Improve this answer
Follow
answered Sep 21, 2015 at 16:38
heb-NR's user avatar
heb-NR
31755 silver badges1313 bronze badges
Add a comment

11


This is the way I updated the master branch

This kind of error occurs commonly after deleting the initial code on your project

So, go ahead, first of all, verify the actual remote version, then remove the origin add the comment, and copy the repo URL into the project files.

$ git remote -v
$ git remote rm origin
$ git commit -m "your commit"
$ git remote add origin https://github.com/user/repo.git
$ git push -f origin master
Share
Improve this answer
Follow
edited Dec 13, 2020 at 23:54
answered Jul 6, 2020 at 16:12
Jose Antonio's user avatar
Jose Antonio
8251414 silver badges2525 bronze badges
1
Try adding explanations to your answer in a way that addresses the question and attempts to help a reader understand. Currently, it just reads like some anecdote and wouldn't even work in the general case (e.g. https://github.com/ is the website root and a git repo) – 
Kache
 Jul 7, 2020 at 5:38
Add a comment

5


if you add your remote repository by using git clone then follow the steps:-

git clone <repo_url> then

git init

git add * *means add all files

git commit -m 'your commit'

git remote -v for check any branch run or not if not then nothing show then we add or fetch the repository. "fetch first". You need to run git pull origin <branch> or git pull -r origin <branch> before a next push.

then

git remote add origin <git url>
 git pull -r origin master
git push -u origin master```
Share
Improve this answer
Follow
answered May 13, 2020 at 11:49
md sha's user avatar
md sha
5111 silver badge11 bronze badge
Add a comment

3


Make sure the config file at .git is correct...Check URL & Make sure your using the correct protocol for your keys ...ProjectWorkspace/.git/config

  ~Wrong url for git@bitbucket
[core]
    repositoryformatversion = 0
    filemode = true
    bare = false
    logallrefupdates = true
[remote "origin"]
    url = gitbucket.org:Prezyack/project-one-hello.git
    fetch = +refs/heads/*:refs/remotes/origin/*

 ~Wrong URL for SSH...
[core]
    repositoryformatversion = 0
    filemode = true
    bare = false
    logallrefupdates = true
    ignorecase = true
    precomposeunicode = true
[remote "origin"]
    fetch = +refs/heads/*:refs/remotes/origin/*
    url = https://emmap1@bitbucket.org/emmap1/bitbucketspacestation.git
[branch "master"]
    remote = origin
    merge = refs/heads/master
We are looking at the URL... e.g: For bitbucket, expect git@bitbucket.org....If its gitbucket.org. make the necessary changes.. SAVE Try pushing again.

Share
Improve this answer
Follow
answered Jul 29, 2016 at 12:32
Magere's user avatar
Magere
9966 bronze badges
Add a comment

2


These two steps worked for me!

Step 1:

git remote set-url origin https://github.com/username/example_repo.git
Step 2:

git push --set-upstream -f origin main
Step 3:

your username and password for github

On step 2, -f is actually required because of the rebase, quote from this post.

Share
Improve this answer
Follow
answered Jan 21, 2021 at 13:07
BlueJapan's user avatar
BlueJapan
1,18622 gold badges1313 silver badges1616 bronze badges
Add a comment

2


For me it helps just by removing existing origin (after i created a new repo and few steps). But before check if the origin is exist in your case:

git remote -v
Then check name of origin (usually set by default) and remove it.

git remote remove origin
And use common github commands while pushing repository to add new origin and finally push your code:

git remote add origin https://github.com/username/repository.git
git branch -M main

git push -u origin main
Share
Improve this answer
Follow
edited Oct 17, 2022 at 8:09
answered Aug 5, 2022 at 9:40
user15038732
Add a comment

1


A similar error appears while pulling the changes from the origin. If you are trying in Intellij from the menu options, the pull might not work directly.

Go to terminal and type this command and this should work out: git pull origin master

Share
Improve this answer
Follow
answered Jun 13, 2018 at 7:50
Nikhil Shrivastav's user avatar
Nikhil Shrivastav
7111 silver badge22 bronze badges
Add a comment

1


What fixed this for me was re-setting my origin url:

git remote set-url origin https://github.com/username/example_repo.git

And then I was able to successfully git push my project. I had to do this even though when I viewed my origins with git remote -v, that the urls were same as what I re-set it as.

Share
Improve this answer
Follow
answered Nov 13, 2020 at 4:27
deesolie's user avatar
deesolie
81766 silver badges1717 bronze badges
Add a comment

1


Most probably the issue is that your remote origin is not set.

git add .
git commit -m "Your commit message"
git remote add origin https://repositoryurlpath.git
git push origin master
Extra Tips:

Check if the remote origin is set

git remote -v
Reset the remote origin

git remote remove origin
git remote add origin https://repositoryurlpath.git
Share
Improve this answer
Follow
answered Sep 14, 2021 at 19:26
Erielama's user avatar
Erielama
11111 silver badge33 bronze badges
Add a comment

0


I had the same issue. When I checked my config file I noticed that 'fetch = +refs/heads/:refs/remotes/origin/' was on the same line as 'url = Z:/GIT/REPOS/SEL.git' as shown:

[core]
    repositoryformatversion = 0
    filemode = false
    bare = false
    logallrefupdates = true
    symlinks = false
    ignorecase = true
[remote "origin"]
    url = Z:/GIT/REPOS/SEL.git     fetch = +refs/heads/*:refs/remotes/origin/*
[branch "master"]
    remote = origin
    merge = refs/heads/master
[gui]
    wmstate = normal
    geometry = 1109x563+32+32 216 255
At first I did not think that this would have mattered but after seeing the post by Magere I moved the line and that fixed the problem:

[core]
    repositoryformatversion = 0
    filemode = false
    bare = false
    logallrefupdates = true
    symlinks = false
    ignorecase = true
[remote "origin"]
    url = Z:/GIT/REPOS/SEL.git
    fetch = +refs/heads/*:refs/remotes/origin/*
[branch "master"]
    remote = origin
    merge = refs/heads/master
[gui]
    wmstate = normal
    geometry = 1109x563+32+32 216 255
Share
Improve this answer
Follow
answered Nov 21, 2019 at 21:05
Beaug45's user avatar
Beaug45
111 bronze badge
Add a comment

0


It happens when you push your code from the current location but after cloning any projects Git creates its own different folder so we have to change our current directory to the required directory. If any got these issue. We can solve it by following these easy steps:-

Firstly create an empty folder.
Open Git GUI/Bash or CMD in the empty folder. Open the empty folder and right click and then open Git.
Click on a clone in Bitbucket(after creating your repository) and copy the cloning path of your repository.
Paste it into your Git and Enter.
After cloning, a new folder is created by git.
Change your directory to the new folder that is created by Git after cloning your repository.
Paste/puts your desired projects/files/folder in this folder.
After keeping your all projects files. Again open Git GUI/Bash in the current folder.
Then type these as usual: a.git add --all b. git commit -m "Your Desired Heart Sound" c. git push -u origin master.
Finally after following these steps you push your projects to Bitbucket
Error:-fatal: Not a git repository (or any of the parent directories):

Thanks.

Share
Improve this answer
Follow
answered Feb 22, 2022 at 7:40
Naffy Kausar's user avatar
Naffy Kausar
8122 gold badges22 silver badges99 bronze badges
Add a comment

0


Firstly remote verbose with the following command:

git remote -v
And see the result of something like that:

origin  https://github.com/MahfuzKhandaker/StudyOnline.git (fetch)
origin  https://github.com/MahfuzKhandaker/StudyOnline.git (push)
Then you have to run the following command to remove origin:

git remote remove origin
And finally you have to add origin:

git remote  add origin  https://github.com/MahfuzKhandaker/StudyOnline.git
Then run the command:

git branch -M main
git push -u origin main
Hope this helps!

Share
Improve this answer
Follow
answered Oct 11, 2022 at 17:41
Mahfuz Khandaker's user avatar
Mahfuz Khandaker
41455 silver badges1111 bronze badges
Add a comment

0


You can see the multiple ways to solve but I recommended to trying this first. It works for me perfectly.

    step 1. git remote -v 
    step 2. git remote rm origin
    step 3. git add .
    step 4. git commit -m "your commit"
    step 5. git remote set-url origin https://github.com/<your_github_username>/<repository_name>.git
    step 6. git push --set-upstream -f origin main
Note: if error: No such remote 'origin' this error occurred. then before step 5 use this command -

git remote add origin https://github.com/<your_github_username>/<repository_name>.git
then again start from step 5

Follow this 6 steps, Thanks.

Share
Improve this answer
Follow
edited Mar 18 at 17:20
answered Mar 8 at 16:59
Md Wahiduzzaman Emon's user avatar
Md Wahiduzzaman Emon
59133 silver badges1010 bronze badges
Add a comment

0


you just need add github.com to your host file:

ssh-keygen -f "/home/<user>/.ssh/known_hosts" -R "github.com"
Share
Improve this answer
Follow
answered May 3 at 8:37
Jaber Alshami's user avatar
Jaber Alshami
33633 silver badges1414 bronze badges
Add a comment

-4


Sometimes you don't have a local REF for pushing that branch back to the origin.
Try

git push origin master:master
This explicitly indicates which branch to push to (and from)

Share
Improve this answer
Follow
answered Dec 13, 2018 at 13:25
vsriram92's user avatar
vsriram92
51811 gold badge44 silver badges1515 bronze badges
Add a comment
Highly active question. Earn 10 reputation (not counting the association bonus) in order to answer this question. The reputation requirement helps protect this question from spam and non-answer activity.

Not the answer you're looking for? Browse other questions tagged gitgithubversion-controlbranch or ask your own question.
The Overflow Blog
How to use marketing techniques to build a better resume
How the creator of Angular is dehydrating the web (Ep. 574)
Featured on Meta
AI/ML Tool examples part 3 - Title-Drafting Assistant
We are graduating the updated button styling for vote arrows
Temporary policy: ChatGPT is banned
Stack Overflow will be testing a title-drafting assistant, and we’d like your...
We are graduating the "Related questions using Machine Learning" experiment
The [connect] tag is being burninated
Linked
762
Updates were rejected because the tip of your current branch is behind its remote counterpart
2
Push on GIT and Bitbucket
0
Git - 'origin' does not appear to be a git repository
2
fatal: '~peterI/public_html/public.git' does not appear to be a git repository fatal: Could not read from remote repository
1
Local repository is not able to pull branch from remote repository
0
Change Git Username to Connect to My Remote Repo
2
Trying to pull from github i get error remote: Repository not found
1
I'm trying to do a git fetch. However, I'm receiving an error "remote: Repository not found. fatal: repository not found
0
error: failed to push some refs to 'git@github.com:MyGitHub/foo.git'
0
My project files are not getting pushed to GitHub repository
See more linked questions
Related
27
Git push origin master returns "fatal: No path specified."
0
Fatal error on git push origin master?
92
Git push error: "origin does not appear to be a git repository"
129
fatal: 'origin' does not appear to be a git repository
4
GIT: fatal: Could not read from remote repository when you create new branch
0
fatal: Could not read from remote repository error while git push
6
Git push origin Permission to * denied fatal: Could not read from remote repository
14
fatal- 'origin' does not appear to be a git repository
0
Git push origin master -f : "fatal 'origin' does not appear to be a git repository - fatal Could not read from remote repository."
1
Git push results in "Could not read from remote repository"
Hot Network Questions
Dovecot:/Thunderbird sslv3 alert certificate expired: SSL alert number 45
Should I pre-emptively confess after submitting work that was partially generated by ChatGPT?
What is \DocumentMetadata? What key-value pairs does it take and when should I use it?
How far apart has the sun drifted from Alpha Centari due to the expansion of the universe since its formation?
The Planet of the Ants: Giant Ant Physiology
Placing multiple nodes around a circle
Company wants to see offer letter received from another company to match salary
"Solvitas perambulum": Is this real Latin?
How many sorting networks?
What would be an example of something digital which isn't electronic?
Why did it take so long to invent telescopes given glass was used 4000 years ago in Mesopotamia?
Resultant of two polynomials
Why is Killiniq island divided between Nunavut and Labrador?
How can a passenger have opened an emergency exit on an Airbus A321 in flight?
Why did Trinity not take Neo to Morpheus when meeting him in the club?
How change the data arrangement in a list?
Is it appropriate to cite vulgar websites used for gathering data?
Did Nelson Mandela read The Economist in prison?
Can you pack these tetracubes to form a rectangular block with at least one odd side length?
Need help figuring out circuit board design
How to handle it if one player wants to take a risky course of action that nobody else wants?
Is there anything important to know about flying at ~9000ft for the first time?
Demarcated "Proof Idea"
Is Russian the most diverged Slavic language?
 Question feed

STACK OVERFLOW
Questions
Help
PRODUCTS
Teams
Advertising
Collectives
Talent
COMPANY
About
Press
Work Here
Legal
Privacy Policy
Terms of Service
Contact Us
Cookie Settings
Cookie Policy
STACK EXCHANGE NETWORK
Technology
Culture & recreation
Life & arts
Science
Professional
Business
API
DataHowever, at some point, I created a new branch locally called add-calendar-model in case next steps of the app development would go south...

... which is exactly what happened.

However, despite many attempts, I did not manage to get the initial code — i.e. the code from before I created the new branch — from the master branch to my local repository.

So, I decided to manually delete all the files from my local repository and git clone my master branch from GitHub.

This way, I got all my files back, but now, I cannot push any more to the remote repository.

Any time I try to run git push origin add-calendar-model or git push origin master, I get the following error:

fatal: 'origin' does not appear to be a git repository
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
I am not very comfortable with Git and GitHub, as you may have guessed by now, and I have to admit that I have no clue about how to fix this.

Any idea?

gitgithubversion-controlbranch
Share
Improve this question
Follow
asked Aug 27, 2015 at 0:03
Thibaud Clement's user avatar
Thibaud Clement
6,5271010 gold badges5050 silver badges103103 bronze badges
2
I had a similar error, But my problem was I had initialized git in the parent directory of the current folder I was trying it. Just in case if anyone is still facing, can look where the git is initialized and then try again. – 
Himanshu Kriplani
 Apr 17, 2020 at 2:39
Add a comment
17 Answers
Sorted by:

Highest score (default)

321


First, check that your origin is set by running

git remote -v
This should show you all of the push / fetch remotes for the project.

If this returns with no output, skip to last code block.

Verify remote name / address

If this returns showing that you have remotes set, check that the name of the remote matches the remote you are using in your commands.

$git remote -v
myOrigin ssh://git@example.com:1234/myRepo.git (fetch)
myOrigin ssh://git@example.com:1234/myRepo.git (push)

# this will fail because `origin` is not set
$git push origin main

# you need to use
$git push myOrigin main
If you want to rename the remote or change the remote's URL, you'll want to first remove the old remote, and then add the correct one.

Remove the old remote

$git remote remove myOrigin
Add missing remote

You can then add in the proper remote using

$git remote add origin ssh://git@example.com:1234/myRepo.git

# this will now work as expected
$git push origin main
Share
Improve this answer
Follow
edited Nov 4, 2021 at 20:14
Simo Pelle's user avatar
Simo Pelle
14111 silver badge1010 bronze badges
answered Aug 27, 2015 at 0:06
Matt Clark's user avatar
Matt Clark
27.6k1919 gold badges6767 silver badges122122 bronze badges
It worked for me without the ssh:// in front of git@example.com:1234/myRepo.git – 
Carol-Theodor Pelu
 Jul 16, 2018 at 7:05
I was reading this question if you could help with the new repository push error as well? – 
StaticVariable
 Sep 3, 2018 at 7:04
I renamed my remote branch from upstream to origin and it caused the error, after completely deleting the remote reference using git remote remove origin and then adding it again using git remote add origin <url> then it worked fine – 
Uriahs Victor
 Jun 29, 2021 at 18:31
This worked for me, with a slight tweak. git remote -v was showing that my origin was git@bitbucket.org/[repo].git. After removing that origin, I replaced it with just bitbucket.org/[repo].git, and this worked. To clarify, I got rid of the "git@" and just put in the repo URL without a user, prompting it to ask for a user for all push/pull commands (which is what I needed anyway). – 
Bad Programmer
 Aug 3, 2022 at 17:59
Add a comment

31


It works for me.

git remote add origin https://github.com/repo.git
git push origin master
add the repository URL to the origin in the local working directory

Share
Improve this answer
Follow
answered Jul 21, 2020 at 8:22
vinod's user avatar
vinod
52555 silver badges1010 bronze badges
2
When I removed the *.git in the end it worked for me: git remote add origin https://github.com/user/repo – 
Joel Wiklund
 Nov 5, 2022 at 7:12
Add a comment

16


As Matt Clark stated above

However, origin might not be set, so skip the deleting step and simply attempting to add can clear this up.

git remote add origin <"clone">
Where "clone" is simply going into your GitHub repo and copying the "HTTPS clone URL" and pasting into GitBash

Share
Improve this answer
Follow
answered Sep 21, 2015 at 16:38
heb-NR's user avatar
heb-NR
31755 silver badges1313 bronze badges
Add a comment

11


This is the way I updated the master branch

This kind of error occurs commonly after deleting the initial code on your project

So, go ahead, first of all, verify the actual remote version, then remove the origin add the comment, and copy the repo URL into the project files.

$ git remote -v
$ git remote rm origin
$ git commit -m "your commit"
$ git remote add origin https://github.com/user/repo.git
$ git push -f origin master
Share
Improve this answer
Follow
edited Dec 13, 2020 at 23:54
answered Jul 6, 2020 at 16:12
Jose Antonio's user avatar
Jose Antonio
8251414 silver badges2525 bronze badges
1
Try adding explanations to your answer in a way that addresses the question and attempts to help a reader understand. Currently, it just reads like some anecdote and wouldn't even work in the general case (e.g. https://github.com/ is the website root and a git repo) – 
Kache
 Jul 7, 2020 at 5:38
Add a comment

5


if you add your remote repository by using git clone then follow the steps:-

git clone <repo_url> then

git init

git add * *means add all files

git commit -m 'your commit'

git remote -v for check any branch run or not if not then nothing show then we add or fetch the repository. "fetch first". You need to run git pull origin <branch> or git pull -r origin <branch> before a next push.

then

git remote add origin <git url>
 git pull -r origin master
git push -u origin master```
Share
Improve this answer
Follow
answered May 13, 2020 at 11:49
md sha's user avatar
md sha
5111 silver badge11 bronze badge
Add a comment

3


Make sure the config file at .git is correct...Check URL & Make sure your using the correct protocol for your keys ...ProjectWorkspace/.git/config

  ~Wrong url for git@bitbucket
[core]
    repositoryformatversion = 0
    filemode = true
    bare = false
    logallrefupdates = true
[remote "origin"]
    url = gitbucket.org:Prezyack/project-one-hello.git
    fetch = +refs/heads/*:refs/remotes/origin/*

 ~Wrong URL for SSH...
[core]
    repositoryformatversion = 0
    filemode = true
    bare = false
    logallrefupdates = true
    ignorecase = true
    precomposeunicode = true
[remote "origin"]
    fetch = +refs/heads/*:refs/remotes/origin/*
    url = https://emmap1@bitbucket.org/emmap1/bitbucketspacestation.git
[branch "master"]
    remote = origin
    merge = refs/heads/master
We are looking at the URL... e.g: For bitbucket, expect git@bitbucket.org....If its gitbucket.org. make the necessary changes.. SAVE Try pushing again.

Share
Improve this answer
Follow
answered Jul 29, 2016 at 12:32
Magere's user avatar
Magere
9966 bronze badges
Add a comment

2


These two steps worked for me!

Step 1:

git remote set-url origin https://github.com/username/example_repo.git
Step 2:

git push --set-upstream -f origin main
Step 3:

your username and password for github

On step 2, -f is actually required because of the rebase, quote from this post.

Share
Improve this answer
Follow
answered Jan 21, 2021 at 13:07
BlueJapan's user avatar
BlueJapan
1,18622 gold badges1313 silver badges1616 bronze badges
Add a comment

2


For me it helps just by removing existing origin (after i created a new repo and few steps). But before check if the origin is exist in your case:

git remote -v
Then check name of origin (usually set by default) and remove it.

git remote remove origin
And use common github commands while pushing repository to add new origin and finally push your code:

git remote add origin https://github.com/username/repository.git
git branch -M main

git push -u origin main
Share
Improve this answer
Follow
edited Oct 17, 2022 at 8:09
answered Aug 5, 2022 at 9:40
user15038732
Add a comment

1


A similar error appears while pulling the changes from the origin. If you are trying in Intellij from the menu options, the pull might not work directly.

Go to terminal and type this command and this should work out: git pull origin master

Share
Improve this answer
Follow
answered Jun 13, 2018 at 7:50
Nikhil Shrivastav's user avatar
Nikhil Shrivastav
7111 silver badge22 bronze badges
Add a comment

1


What fixed this for me was re-setting my origin url:

git remote set-url origin https://github.com/username/example_repo.git

And then I was able to successfully git push my project. I had to do this even though when I viewed my origins with git remote -v, that the urls were same as what I re-set it as.

Share
Improve this answer
Follow
answered Nov 13, 2020 at 4:27
deesolie's user avatar
deesolie
81766 silver badges1717 bronze badges
Add a comment

1


Most probably the issue is that your remote origin is not set.

git add .
git commit -m "Your commit message"
git remote add origin https://repositoryurlpath.git
git push origin master
Extra Tips:

Check if the remote origin is set

git remote -v
Reset the remote origin

git remote remove origin
git remote add origin https://repositoryurlpath.git
Share
Improve this answer
Follow
answered Sep 14, 2021 at 19:26
Erielama's user avatar
Erielama
11111 silver badge33 bronze badges
Add a comment

0


I had the same issue. When I checked my config file I noticed that 'fetch = +refs/heads/:refs/remotes/origin/' was on the same line as 'url = Z:/GIT/REPOS/SEL.git' as shown:

[core]
    repositoryformatversion = 0
    filemode = false
    bare = false
    logallrefupdates = true
    symlinks = false
    ignorecase = true
[remote "origin"]
    url = Z:/GIT/REPOS/SEL.git     fetch = +refs/heads/*:refs/remotes/origin/*
[branch "master"]
    remote = origin
    merge = refs/heads/master
[gui]
    wmstate = normal
    geometry = 1109x563+32+32 216 255
At first I did not think that this would have mattered but after seeing the post by Magere I moved the line and that fixed the problem:

[core]
    repositoryformatversion = 0
    filemode = false
    bare = false
    logallrefupdates = true
    symlinks = false
    ignorecase = true
[remote "origin"]
    url = Z:/GIT/REPOS/SEL.git
    fetch = +refs/heads/*:refs/remotes/origin/*
[branch "master"]
    remote = origin
    merge = refs/heads/master
[gui]
    wmstate = normal
    geometry = 1109x563+32+32 216 255
Share
Improve this answer
Follow
answered Nov 21, 2019 at 21:05
Beaug45's user avatar
Beaug45
111 bronze badge
Add a comment

0


It happens when you push your code from the current location but after cloning any projects Git creates its own different folder so we have to change our current directory to the required directory. If any got these issue. We can solve it by following these easy steps:-

Firstly create an empty folder.
Open Git GUI/Bash or CMD in the empty folder. Open the empty folder and right click and then open Git.
Click on a clone in Bitbucket(after creating your repository) and copy the cloning path of your repository.
Paste it into your Git and Enter.
After cloning, a new folder is created by git.
Change your directory to the new folder that is created by Git after cloning your repository.
Paste/puts your desired projects/files/folder in this folder.
After keeping your all projects files. Again open Git GUI/Bash in the current folder.
Then type these as usual: a.git add --all b. git commit -m "Your Desired Heart Sound" c. git push -u origin master.
Finally after following these steps you push your projects to Bitbucket
Error:-fatal: Not a git repository (or any of the parent directories):

Thanks.

Share
Improve this answer
Follow
answered Feb 22, 2022 at 7:40
Naffy Kausar's user avatar
Naffy Kausar
8122 gold badges22 silver badges99 bronze badges
Add a comment

0


Firstly remote verbose with the following command:

git remote -v
And see the result of something like that:

origin  https://github.com/MahfuzKhandaker/StudyOnline.git (fetch)
origin  https://github.com/MahfuzKhandaker/StudyOnline.git (push)
Then you have to run the following command to remove origin:

git remote remove origin
And finally you have to add origin:

git remote  add origin  https://github.com/MahfuzKhandaker/StudyOnline.git
Then run the command:

git branch -M main
git push -u origin main
Hope this helps!

Share
Improve this answer
Follow
answered Oct 11, 2022 at 17:41
Mahfuz Khandaker's user avatar
Mahfuz Khandaker
41455 silver badges1111 bronze badges
Add a comment

0


You can see the multiple ways to solve but I recommended to trying this first. It works for me perfectly.

    step 1. git remote -v 
    step 2. git remote rm origin
    step 3. git add .
    step 4. git commit -m "your commit"
    step 5. git remote set-url origin https://github.com/<your_github_username>/<repository_name>.git
    step 6. git push --set-upstream -f origin main
Note: if error: No such remote 'origin' this error occurred. then before step 5 use this command -

git remote add origin https://github.com/<your_github_username>/<repository_name>.git
then again start from step 5

Follow this 6 steps, Thanks.

Share
Improve this answer
Follow
edited Mar 18 at 17:20
answered Mar 8 at 16:59
Md Wahiduzzaman Emon's user avatar
Md Wahiduzzaman Emon
59133 silver badges1010 bronze badges
Add a comment

0


you just need add github.com to your host file:

ssh-keygen -f "/home/<user>/.ssh/known_hosts" -R "github.com"
Share
Improve this answer
Follow
answered May 3 at 8:37
Jaber Alshami's user avatar
Jaber Alshami
33633 silver badges1414 bronze badges
Add a comment

-4


Sometimes you don't have a local REF for pushing that branch back to the origin.
Try

git push origin master:master
This explicitly indicates which branch to push to (and from)

Share
Improve this answer
Follow
answered Dec 13, 2018 at 13:25
vsriram92's user avatar
vsriram92
51811 gold badge44 silver badges1515 bronze badges
Add a comment
Highly active question. Earn 10 reputation (not counting the association bonus) in order to answer this question. The reputation requirement helps protect this question from spam and non-answer activity.

Not the answer you're looking for? Browse other questions tagged gitgithubversion-controlbranch or ask your own question.
The Overflow Blog
How to use marketing techniques to build a better resume
How the creator of Angular is dehydrating the web (Ep. 574)
Featured on Meta
AI/ML Tool examples part 3 - Title-Drafting Assistant
We are graduating the updated button styling for vote arrows
Temporary policy: ChatGPT is banned
Stack Overflow will be testing a title-drafting assistant, and we’d like your...
We are graduating the "Related questions using Machine Learning" experiment
The [connect] tag is being burninated
Linked
762
Updates were rejected because the tip of your current branch is behind its remote counterpart
2
Push on GIT and Bitbucket
0
Git - 'origin' does not appear to be a git repository
2
fatal: '~peterI/public_html/public.git' does not appear to be a git repository fatal: Could not read from remote repository
1
Local repository is not able to pull branch from remote repository
0
Change Git Username to Connect to My Remote Repo
2
Trying to pull from github i get error remote: Repository not found
1
I'm trying to do a git fetch. However, I'm receiving an error "remote: Repository not found. fatal: repository not found
0
error: failed to push some refs to 'git@github.com:MyGitHub/foo.git'
0
My project files are not getting pushed to GitHub repository
See more linked questions
Related
27
Git push origin master returns "fatal: No path specified."
0
Fatal error on git push origin master?
92
Git push error: "origin does not appear to be a git repository"
129
fatal: 'origin' does not appear to be a git repository
4
GIT: fatal: Could not read from remote repository when you create new branch
0
fatal: Could not read from remote repository error while git push
6
Git push origin Permission to * denied fatal: Could not read from remote repository
14
fatal- 'origin' does not appear to be a git repository
0
Git push origin master -f : "fatal 'origin' does not appear to be a git repository - fatal Could not read from remote repository."
1
Git push results in "Could not read from remote repository"
Hot Network Questions
Dovecot:/Thunderbird sslv3 alert certificate expired: SSL alert number 45
Should I pre-emptively confess after submitting work that was partially generated by ChatGPT?
What is \DocumentMetadata? What key-value pairs does it take and when should I use it?
How far apart has the sun drifted from Alpha Centari due to the expansion of the universe since its formation?
The Planet of the Ants: Giant Ant Physiology
Placing multiple nodes around a circle
Company wants to see offer letter received from another company to match salary
"Solvitas perambulum": Is this real Latin?
How many sorting networks?
What would be an example of something digital which isn't electronic?
Why did it take so long to invent telescopes given glass was used 4000 years ago in Mesopotamia?
Resultant of two polynomials
Why is Killiniq island divided between Nunavut and Labrador?
How can a passenger have opened an emergency exit on an Airbus A321 in flight?
Why did Trinity not take Neo to Morpheus when meeting him in the club?
How change the data arrangement in a list?
Is it appropriate to cite vulgar websites used for gathering data?
Did Nelson Mandela read The Economist in prison?
Can you pack these tetracubes to form a rectangular block with at least one odd side length?
Need help figuring out circuit board design
How to handle it if one player wants to take a risky course of action that nobody else wants?
Is there anything important to know about flying at ~9000ft for the first time?
Demarcated "Proof Idea"
Is Russian the most diverged Slavic language?
 Question feed

STACK OVERFLOW
Questions
Help
PRODUCTS
Teams
Advertising
Collectives
Talent
COMPANY
About
Press
Work Here
Legal
Privacy Policy
Terms of Service
Contact Us
Cookie Settings
Cookie Policy
STACK EXCHANGE NETWORK
Technology
Culture & recreation
Life & arts
Science
Professional
Business
API
DataHowever, at some point, I created a new branch locally called add-calendar-model in case next steps of the app development would go south...

... which is exactly what happened.

However, despite many attempts, I did not manage to get the initial code — i.e. the code from before I created the new branch — from the master branch to my local repository.

So, I decided to manually delete all the files from my local repository and git clone my master branch from GitHub.

This way, I got all my files back, but now, I cannot push any more to the remote repository.

Any time I try to run git push origin add-calendar-model or git push origin master, I get the following error:

fatal: 'origin' does not appear to be a git repository
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
I am not very comfortable with Git and GitHub, as you may have guessed by now, and I have to admit that I have no clue about how to fix this.

Any idea?

gitgithubversion-controlbranch
Share
Improve this question
Follow
asked Aug 27, 2015 at 0:03
Thibaud Clement's user avatar
Thibaud Clement
6,5271010 gold badges5050 silver badges103103 bronze badges
2
I had a similar error, But my problem was I had initialized git in the parent directory of the current folder I was trying it. Just in case if anyone is still facing, can look where the git is initialized and then try again. – 
Himanshu Kriplani
 Apr 17, 2020 at 2:39
Add a comment
17 Answers
Sorted by:

Highest score (default)

321


First, check that your origin is set by running

git remote -v
This should show you all of the push / fetch remotes for the project.

If this returns with no output, skip to last code block.

Verify remote name / address

If this returns showing that you have remotes set, check that the name of the remote matches the remote you are using in your commands.

$git remote -v
myOrigin ssh://git@example.com:1234/myRepo.git (fetch)
myOrigin ssh://git@example.com:1234/myRepo.git (push)

# this will fail because `origin` is not set
$git push origin main

# you need to use
$git push myOrigin main
If you want to rename the remote or change the remote's URL, you'll want to first remove the old remote, and then add the correct one.

Remove the old remote

$git remote remove myOrigin
Add missing remote

You can then add in the proper remote using

$git remote add origin ssh://git@example.com:1234/myRepo.git

# this will now work as expected
$git push origin main
Share
Improve this answer
Follow
edited Nov 4, 2021 at 20:14
Simo Pelle's user avatar
Simo Pelle
14111 silver badge1010 bronze badges
answered Aug 27, 2015 at 0:06
Matt Clark's user avatar
Matt Clark
27.6k1919 gold badges6767 silver badges122122 bronze badges
It worked for me without the ssh:// in front of git@example.com:1234/myRepo.git – 
Carol-Theodor Pelu
 Jul 16, 2018 at 7:05
I was reading this question if you could help with the new repository push error as well? – 
StaticVariable
 Sep 3, 2018 at 7:04
I renamed my remote branch from upstream to origin and it caused the error, after completely deleting the remote reference using git remote remove origin and then adding it again using git remote add origin <url> then it worked fine – 
Uriahs Victor
 Jun 29, 2021 at 18:31
This worked for me, with a slight tweak. git remote -v was showing that my origin was git@bitbucket.org/[repo].git. After removing that origin, I replaced it with just bitbucket.org/[repo].git, and this worked. To clarify, I got rid of the "git@" and just put in the repo URL without a user, prompting it to ask for a user for all push/pull commands (which is what I needed anyway). – 
Bad Programmer
 Aug 3, 2022 at 17:59
Add a comment

31


It works for me.

git remote add origin https://github.com/repo.git
git push origin master
add the repository URL to the origin in the local working directory

Share
Improve this answer
Follow
answered Jul 21, 2020 at 8:22
vinod's user avatar
vinod
52555 silver badges1010 bronze badges
2
When I removed the *.git in the end it worked for me: git remote add origin https://github.com/user/repo – 
Joel Wiklund
 Nov 5, 2022 at 7:12
Add a comment

16


As Matt Clark stated above

However, origin might not be set, so skip the deleting step and simply attempting to add can clear this up.

git remote add origin <"clone">
Where "clone" is simply going into your GitHub repo and copying the "HTTPS clone URL" and pasting into GitBash

Share
Improve this answer
Follow
answered Sep 21, 2015 at 16:38
heb-NR's user avatar
heb-NR
31755 silver badges1313 bronze badges
Add a comment

11


This is the way I updated the master branch

This kind of error occurs commonly after deleting the initial code on your project

So, go ahead, first of all, verify the actual remote version, then remove the origin add the comment, and copy the repo URL into the project files.

$ git remote -v
$ git remote rm origin
$ git commit -m "your commit"
$ git remote add origin https://github.com/user/repo.git
$ git push -f origin master
Share
Improve this answer
Follow
edited Dec 13, 2020 at 23:54
answered Jul 6, 2020 at 16:12
Jose Antonio's user avatar
Jose Antonio
8251414 silver badges2525 bronze badges
1
Try adding explanations to your answer in a way that addresses the question and attempts to help a reader understand. Currently, it just reads like some anecdote and wouldn't even work in the general case (e.g. https://github.com/ is the website root and a git repo) – 
Kache
 Jul 7, 2020 at 5:38
Add a comment

5


if you add your remote repository by using git clone then follow the steps:-

git clone <repo_url> then

git init

git add * *means add all files

git commit -m 'your commit'

git remote -v for check any branch run or not if not then nothing show then we add or fetch the repository. "fetch first". You need to run git pull origin <branch> or git pull -r origin <branch> before a next push.

then

git remote add origin <git url>
 git pull -r origin master
git push -u origin master```
Share
Improve this answer
Follow
answered May 13, 2020 at 11:49
md sha's user avatar
md sha
5111 silver badge11 bronze badge
Add a comment

3


Make sure the config file at .git is correct...Check URL & Make sure your using the correct protocol for your keys ...ProjectWorkspace/.git/config

  ~Wrong url for git@bitbucket
[core]
    repositoryformatversion = 0
    filemode = true
    bare = false
    logallrefupdates = true
[remote "origin"]
    url = gitbucket.org:Prezyack/project-one-hello.git
    fetch = +refs/heads/*:refs/remotes/origin/*

 ~Wrong URL for SSH...
[core]
    repositoryformatversion = 0
    filemode = true
    bare = false
    logallrefupdates = true
    ignorecase = true
    precomposeunicode = true
[remote "origin"]
    fetch = +refs/heads/*:refs/remotes/origin/*
    url = https://emmap1@bitbucket.org/emmap1/bitbucketspacestation.git
[branch "master"]
    remote = origin
    merge = refs/heads/master
We are looking at the URL... e.g: For bitbucket, expect git@bitbucket.org....If its gitbucket.org. make the necessary changes.. SAVE Try pushing again.

Share
Improve this answer
Follow
answered Jul 29, 2016 at 12:32
Magere's user avatar
Magere
9966 bronze badges
Add a comment

2


These two steps worked for me!

Step 1:

git remote set-url origin https://github.com/username/example_repo.git
Step 2:

git push --set-upstream -f origin main
Step 3:

your username and password for github

On step 2, -f is actually required because of the rebase, quote from this post.

Share
Improve this answer
Follow
answered Jan 21, 2021 at 13:07
BlueJapan's user avatar
BlueJapan
1,18622 gold badges1313 silver badges1616 bronze badges
Add a comment

2


For me it helps just by removing existing origin (after i created a new repo and few steps). But before check if the origin is exist in your case:

git remote -v
Then check name of origin (usually set by default) and remove it.

git remote remove origin
And use common github commands while pushing repository to add new origin and finally push your code:

git remote add origin https://github.com/username/repository.git
git branch -M main

git push -u origin main
Share
Improve this answer
Follow
edited Oct 17, 2022 at 8:09
answered Aug 5, 2022 at 9:40
user15038732
Add a comment

1


A similar error appears while pulling the changes from the origin. If you are trying in Intellij from the menu options, the pull might not work directly.

Go to terminal and type this command and this should work out: git pull origin master

Share
Improve this answer
Follow
answered Jun 13, 2018 at 7:50
Nikhil Shrivastav's user avatar
Nikhil Shrivastav
7111 silver badge22 bronze badges
Add a comment

1


What fixed this for me was re-setting my origin url:

git remote set-url origin https://github.com/username/example_repo.git

And then I was able to successfully git push my project. I had to do this even though when I viewed my origins with git remote -v, that the urls were same as what I re-set it as.

Share
Improve this answer
Follow
answered Nov 13, 2020 at 4:27
deesolie's user avatar
deesolie
81766 silver badges1717 bronze badges
Add a comment

1


Most probably the issue is that your remote origin is not set.

git add .
git commit -m "Your commit message"
git remote add origin https://repositoryurlpath.git
git push origin master
Extra Tips:

Check if the remote origin is set

git remote -v
Reset the remote origin

git remote remove origin
git remote add origin https://repositoryurlpath.git
Share
Improve this answer
Follow
answered Sep 14, 2021 at 19:26
Erielama's user avatar
Erielama
11111 silver badge33 bronze badges
Add a comment

0


I had the same issue. When I checked my config file I noticed that 'fetch = +refs/heads/:refs/remotes/origin/' was on the same line as 'url = Z:/GIT/REPOS/SEL.git' as shown:

[core]
    repositoryformatversion = 0
    filemode = false
    bare = false
    logallrefupdates = true
    symlinks = false
    ignorecase = true
[remote "origin"]
    url = Z:/GIT/REPOS/SEL.git     fetch = +refs/heads/*:refs/remotes/origin/*
[branch "master"]
    remote = origin
    merge = refs/heads/master
[gui]
    wmstate = normal
    geometry = 1109x563+32+32 216 255
At first I did not think that this would have mattered but after seeing the post by Magere I moved the line and that fixed the problem:

[core]
    repositoryformatversion = 0
    filemode = false
    bare = false
    logallrefupdates = true
    symlinks = false
    ignorecase = true
[remote "origin"]
    url = Z:/GIT/REPOS/SEL.git
    fetch = +refs/heads/*:refs/remotes/origin/*
[branch "master"]
    remote = origin
    merge = refs/heads/master
[gui]
    wmstate = normal
    geometry = 1109x563+32+32 216 255
Share
Improve this answer
Follow
answered Nov 21, 2019 at 21:05
Beaug45's user avatar
Beaug45
111 bronze badge
Add a comment

0


It happens when you push your code from the current location but after cloning any projects Git creates its own different folder so we have to change our current directory to the required directory. If any got these issue. We can solve it by following these easy steps:-

Firstly create an empty folder.
Open Git GUI/Bash or CMD in the empty folder. Open the empty folder and right click and then open Git.
Click on a clone in Bitbucket(after creating your repository) and copy the cloning path of your repository.
Paste it into your Git and Enter.
After cloning, a new folder is created by git.
Change your directory to the new folder that is created by Git after cloning your repository.
Paste/puts your desired projects/files/folder in this folder.
After keeping your all projects files. Again open Git GUI/Bash in the current folder.
Then type these as usual: a.git add --all b. git commit -m "Your Desired Heart Sound" c. git push -u origin master.
Finally after following these steps you push your projects to Bitbucket
Error:-fatal: Not a git repository (or any of the parent directories):

Thanks.

Share
Improve this answer
Follow
answered Feb 22, 2022 at 7:40
Naffy Kausar's user avatar
Naffy Kausar
8122 gold badges22 silver badges99 bronze badges
Add a comment

0


Firstly remote verbose with the following command:

git remote -v
And see the result of something like that:

origin  https://github.com/MahfuzKhandaker/StudyOnline.git (fetch)
origin  https://github.com/MahfuzKhandaker/StudyOnline.git (push)
Then you have to run the following command to remove origin:

git remote remove origin
And finally you have to add origin:

git remote  add origin  https://github.com/MahfuzKhandaker/StudyOnline.git
Then run the command:

git branch -M main
git push -u origin main
Hope this helps!

Share
Improve this answer
Follow
answered Oct 11, 2022 at 17:41
Mahfuz Khandaker's user avatar
Mahfuz Khandaker
41455 silver badges1111 bronze badges
Add a comment

0


You can see the multiple ways to solve but I recommended to trying this first. It works for me perfectly.

    step 1. git remote -v 
    step 2. git remote rm origin
    step 3. git add .
    step 4. git commit -m "your commit"
    step 5. git remote set-url origin https://github.com/<your_github_username>/<repository_name>.git
    step 6. git push --set-upstream -f origin main
Note: if error: No such remote 'origin' this error occurred. then before step 5 use this command -

git remote add origin https://github.com/<your_github_username>/<repository_name>.git
then again start from step 5

Follow this 6 steps, Thanks.

Share
Improve this answer
Follow
edited Mar 18 at 17:20
answered Mar 8 at 16:59
Md Wahiduzzaman Emon's user avatar
Md Wahiduzzaman Emon
59133 silver badges1010 bronze badges
Add a comment

0


you just need add github.com to your host file:

ssh-keygen -f "/home/<user>/.ssh/known_hosts" -R "github.com"
Share
Improve this answer
Follow
answered May 3 at 8:37
Jaber Alshami's user avatar
Jaber Alshami
33633 silver badges1414 bronze badges
Add a comment

-4


Sometimes you don't have a local REF for pushing that branch back to the origin.
Try

git push origin master:master
This explicitly indicates which branch to push to (and from)

Share
Improve this answer
Follow
answered Dec 13, 2018 at 13:25
vsriram92's user avatar
vsriram92
51811 gold badge44 silver badges1515 bronze badges
Add a comment
Highly active question. Earn 10 reputation (not counting the association bonus) in order to answer this question. The reputation requirement helps protect this question from spam and non-answer activity.

Not the answer you're looking for? Browse other questions tagged gitgithubversion-controlbranch or ask your own question.
The Overflow Blog
How to use marketing techniques to build a better resume
How the creator of Angular is dehydrating the web (Ep. 574)
Featured on Meta
AI/ML Tool examples part 3 - Title-Drafting Assistant
We are graduating the updated button styling for vote arrows
Temporary policy: ChatGPT is banned
Stack Overflow will be testing a title-drafting assistant, and we’d like your...
We are graduating the "Related questions using Machine Learning" experiment
The [connect] tag is being burninated
Linked
762
Updates were rejected because the tip of your current branch is behind its remote counterpart
2
Push on GIT and Bitbucket
0
Git - 'origin' does not appear to be a git repository
2
fatal: '~peterI/public_html/public.git' does not appear to be a git repository fatal: Could not read from remote repository
1
Local repository is not able to pull branch from remote repository
0
Change Git Username to Connect to My Remote Repo
2
Trying to pull from github i get error remote: Repository not found
1
I'm trying to do a git fetch. However, I'm receiving an error "remote: Repository not found. fatal: repository not found
0
error: failed to push some refs to 'git@github.com:MyGitHub/foo.git'
0
My project files are not getting pushed to GitHub repository
See more linked questions
Related
27
Git push origin master returns "fatal: No path specified."
0
Fatal error on git push origin master?
92
Git push error: "origin does not appear to be a git repository"
129
fatal: 'origin' does not appear to be a git repository
4
GIT: fatal: Could not read from remote repository when you create new branch
0
fatal: Could not read from remote repository error while git push
6
Git push origin Permission to * denied fatal: Could not read from remote repository
14
fatal- 'origin' does not appear to be a git repository
0
Git push origin master -f : "fatal 'origin' does not appear to be a git repository - fatal Could not read from remote repository."
1
Git push results in "Could not read from remote repository"
Hot Network Questions
Dovecot:/Thunderbird sslv3 alert certificate expired: SSL alert number 45
Should I pre-emptively confess after submitting work that was partially generated by ChatGPT?
What is \DocumentMetadata? What key-value pairs does it take and when should I use it?
How far apart has the sun drifted from Alpha Centari due to the expansion of the universe since its formation?
The Planet of the Ants: Giant Ant Physiology
Placing multiple nodes around a circle
Company wants to see offer letter received from another company to match salary
"Solvitas perambulum": Is this real Latin?
How many sorting networks?
What would be an example of something digital which isn't electronic?
Why did it take so long to invent telescopes given glass was used 4000 years ago in Mesopotamia?
Resultant of two polynomials
Why is Killiniq island divided between Nunavut and Labrador?
How can a passenger have opened an emergency exit on an Airbus A321 in flight?
Why did Trinity not take Neo to Morpheus when meeting him in the club?
How change the data arrangement in a list?
Is it appropriate to cite vulgar websites used for gathering data?
Did Nelson Mandela read The Economist in prison?
Can you pack these tetracubes to form a rectangular block with at least one odd side length?
Need help figuring out circuit board design
How to handle it if one player wants to take a risky course of action that nobody else wants?
Is there anything important to know about flying at ~9000ft for the first time?
Demarcated "Proof Idea"
Is Russian the most diverged Slavic language?
 Question feed

STACK OVERFLOW
Questions
Help
PRODUCTS
Teams
Advertising
Collectives
Talent
COMPANY
About
Press
Work Here
Legal
Privacy Policy
Terms of Service
Contact Us
Cookie Settings
Cookie Policy
STACK EXCHANGE NETWORK
Technology
Culture & recreation
Life & arts
Science
Professional
Business
API
DataHowever, at some point, I created a new branch locally called add-calendar-model in case next steps of the app development would go south...

... which is exactly what happened.

However, despite many attempts, I did not manage to get the initial code — i.e. the code from before I created the new branch — from the master branch to my local repository.

So, I decided to manually delete all the files from my local repository and git clone my master branch from GitHub.

This way, I got all my files back, but now, I cannot push any more to the remote repository.

Any time I try to run git push origin add-calendar-model or git push origin master, I get the following error:

fatal: 'origin' does not appear to be a git repository
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
I am not very comfortable with Git and GitHub, as you may have guessed by now, and I have to admit that I have no clue about how to fix this.

Any idea?

gitgithubversion-controlbranch
Share
Improve this question
Follow
asked Aug 27, 2015 at 0:03
Thibaud Clement's user avatar
Thibaud Clement
6,5271010 gold badges5050 silver badges103103 bronze badges
2
I had a similar error, But my problem was I had initialized git in the parent directory of the current folder I was trying it. Just in case if anyone is still facing, can look where the git is initialized and then try again. – 
Himanshu Kriplani
 Apr 17, 2020 at 2:39
Add a comment
17 Answers
Sorted by:

Highest score (default)

321


First, check that your origin is set by running

git remote -v
This should show you all of the push / fetch remotes for the project.

If this returns with no output, skip to last code block.

Verify remote name / address

If this returns showing that you have remotes set, check that the name of the remote matches the remote you are using in your commands.

$git remote -v
myOrigin ssh://git@example.com:1234/myRepo.git (fetch)
myOrigin ssh://git@example.com:1234/myRepo.git (push)

# this will fail because `origin` is not set
$git push origin main

# you need to use
$git push myOrigin main
If you want to rename the remote or change the remote's URL, you'll want to first remove the old remote, and then add the correct one.

Remove the old remote

$git remote remove myOrigin
Add missing remote

You can then add in the proper remote using

$git remote add origin ssh://git@example.com:1234/myRepo.git

# this will now work as expected
$git push origin main
Share
Improve this answer
Follow
edited Nov 4, 2021 at 20:14
Simo Pelle's user avatar
Simo Pelle
14111 silver badge1010 bronze badges
answered Aug 27, 2015 at 0:06
Matt Clark's user avatar
Matt Clark
27.6k1919 gold badges6767 silver badges122122 bronze badges
It worked for me without the ssh:// in front of git@example.com:1234/myRepo.git – 
Carol-Theodor Pelu
 Jul 16, 2018 at 7:05
I was reading this question if you could help with the new repository push error as well? – 
StaticVariable
 Sep 3, 2018 at 7:04
I renamed my remote branch from upstream to origin and it caused the error, after completely deleting the remote reference using git remote remove origin and then adding it again using git remote add origin <url> then it worked fine – 
Uriahs Victor
 Jun 29, 2021 at 18:31
This worked for me, with a slight tweak. git remote -v was showing that my origin was git@bitbucket.org/[repo].git. After removing that origin, I replaced it with just bitbucket.org/[repo].git, and this worked. To clarify, I got rid of the "git@" and just put in the repo URL without a user, prompting it to ask for a user for all push/pull commands (which is what I needed anyway). – 
Bad Programmer
 Aug 3, 2022 at 17:59
Add a comment

31


It works for me.

git remote add origin https://github.com/repo.git
git push origin master
add the repository URL to the origin in the local working directory

Share
Improve this answer
Follow
answered Jul 21, 2020 at 8:22
vinod's user avatar
vinod
52555 silver badges1010 bronze badges
2
When I removed the *.git in the end it worked for me: git remote add origin https://github.com/user/repo – 
Joel Wiklund
 Nov 5, 2022 at 7:12
Add a comment

16


As Matt Clark stated above

However, origin might not be set, so skip the deleting step and simply attempting to add can clear this up.

git remote add origin <"clone">
Where "clone" is simply going into your GitHub repo and copying the "HTTPS clone URL" and pasting into GitBash

Share
Improve this answer
Follow
answered Sep 21, 2015 at 16:38
heb-NR's user avatar
heb-NR
31755 silver badges1313 bronze badges
Add a comment

11


This is the way I updated the master branch

This kind of error occurs commonly after deleting the initial code on your project

So, go ahead, first of all, verify the actual remote version, then remove the origin add the comment, and copy the repo URL into the project files.

$ git remote -v
$ git remote rm origin
$ git commit -m "your commit"
$ git remote add origin https://github.com/user/repo.git
$ git push -f origin master
Share
Improve this answer
Follow
edited Dec 13, 2020 at 23:54
answered Jul 6, 2020 at 16:12
Jose Antonio's user avatar
Jose Antonio
8251414 silver badges2525 bronze badges
1
Try adding explanations to your answer in a way that addresses the question and attempts to help a reader understand. Currently, it just reads like some anecdote and wouldn't even work in the general case (e.g. https://github.com/ is the website root and a git repo) – 
Kache
 Jul 7, 2020 at 5:38
Add a comment

5


if you add your remote repository by using git clone then follow the steps:-

git clone <repo_url> then

git init

git add * *means add all files

git commit -m 'your commit'

git remote -v for check any branch run or not if not then nothing show then we add or fetch the repository. "fetch first". You need to run git pull origin <branch> or git pull -r origin <branch> before a next push.

then

git remote add origin <git url>
 git pull -r origin master
git push -u origin master```
Share
Improve this answer
Follow
answered May 13, 2020 at 11:49
md sha's user avatar
md sha
5111 silver badge11 bronze badge
Add a comment

3


Make sure the config file at .git is correct...Check URL & Make sure your using the correct protocol for your keys ...ProjectWorkspace/.git/config

  ~Wrong url for git@bitbucket
[core]
    repositoryformatversion = 0
    filemode = true
    bare = false
    logallrefupdates = true
[remote "origin"]
    url = gitbucket.org:Prezyack/project-one-hello.git
    fetch = +refs/heads/*:refs/remotes/origin/*

 ~Wrong URL for SSH...
[core]
    repositoryformatversion = 0
    filemode = true
    bare = false
    logallrefupdates = true
    ignorecase = true
    precomposeunicode = true
[remote "origin"]
    fetch = +refs/heads/*:refs/remotes/origin/*
    url = https://emmap1@bitbucket.org/emmap1/bitbucketspacestation.git
[branch "master"]
    remote = origin
    merge = refs/heads/master
We are looking at the URL... e.g: For bitbucket, expect git@bitbucket.org....If its gitbucket.org. make the necessary changes.. SAVE Try pushing again.

Share
Improve this answer
Follow
answered Jul 29, 2016 at 12:32
Magere's user avatar
Magere
9966 bronze badges
Add a comment

2


These two steps worked for me!

Step 1:

git remote set-url origin https://github.com/username/example_repo.git
Step 2:

git push --set-upstream -f origin main
Step 3:

your username and password for github

On step 2, -f is actually required because of the rebase, quote from this post.

Share
Improve this answer
Follow
answered Jan 21, 2021 at 13:07
BlueJapan's user avatar
BlueJapan
1,18622 gold badges1313 silver badges1616 bronze badges
Add a comment

2


For me it helps just by removing existing origin (after i created a new repo and few steps). But before check if the origin is exist in your case:

git remote -v
Then check name of origin (usually set by default) and remove it.

git remote remove origin
And use common github commands while pushing repository to add new origin and finally push your code:

git remote add origin https://github.com/username/repository.git
git branch -M main

git push -u origin main
Share
Improve this answer
Follow
edited Oct 17, 2022 at 8:09
answered Aug 5, 2022 at 9:40
user15038732
Add a comment

1


A similar error appears while pulling the changes from the origin. If you are trying in Intellij from the menu options, the pull might not work directly.

Go to terminal and type this command and this should work out: git pull origin master

Share
Improve this answer
Follow
answered Jun 13, 2018 at 7:50
Nikhil Shrivastav's user avatar
Nikhil Shrivastav
7111 silver badge22 bronze badges
Add a comment

1


What fixed this for me was re-setting my origin url:

git remote set-url origin https://github.com/username/example_repo.git

And then I was able to successfully git push my project. I had to do this even though when I viewed my origins with git remote -v, that the urls were same as what I re-set it as.

Share
Improve this answer
Follow
answered Nov 13, 2020 at 4:27
deesolie's user avatar
deesolie
81766 silver badges1717 bronze badges
Add a comment

1


Most probably the issue is that your remote origin is not set.

git add .
git commit -m "Your commit message"
git remote add origin https://repositoryurlpath.git
git push origin master
Extra Tips:

Check if the remote origin is set

git remote -v
Reset the remote origin

git remote remove origin
git remote add origin https://repositoryurlpath.git
Share
Improve this answer
Follow
answered Sep 14, 2021 at 19:26
Erielama's user avatar
Erielama
11111 silver badge33 bronze badges
Add a comment

0


I had the same issue. When I checked my config file I noticed that 'fetch = +refs/heads/:refs/remotes/origin/' was on the same line as 'url = Z:/GIT/REPOS/SEL.git' as shown:

[core]
    repositoryformatversion = 0
    filemode = false
    bare = false
    logallrefupdates = true
    symlinks = false
    ignorecase = true
[remote "origin"]
    url = Z:/GIT/REPOS/SEL.git     fetch = +refs/heads/*:refs/remotes/origin/*
[branch "master"]
    remote = origin
    merge = refs/heads/master
[gui]
    wmstate = normal
    geometry = 1109x563+32+32 216 255
At first I did not think that this would have mattered but after seeing the post by Magere I moved the line and that fixed the problem:

[core]
    repositoryformatversion = 0
    filemode = false
    bare = false
    logallrefupdates = true
    symlinks = false
    ignorecase = true
[remote "origin"]
    url = Z:/GIT/REPOS/SEL.git
    fetch = +refs/heads/*:refs/remotes/origin/*
[branch "master"]
    remote = origin
    merge = refs/heads/master
[gui]
    wmstate = normal
    geometry = 1109x563+32+32 216 255
Share
Improve this answer
Follow
answered Nov 21, 2019 at 21:05
Beaug45's user avatar
Beaug45
111 bronze badge
Add a comment

0


It happens when you push your code from the current location but after cloning any projects Git creates its own different folder so we have to change our current directory to the required directory. If any got these issue. We can solve it by following these easy steps:-

Firstly create an empty folder.
Open Git GUI/Bash or CMD in the empty folder. Open the empty folder and right click and then open Git.
Click on a clone in Bitbucket(after creating your repository) and copy the cloning path of your repository.
Paste it into your Git and Enter.
After cloning, a new folder is created by git.
Change your directory to the new folder that is created by Git after cloning your repository.
Paste/puts your desired projects/files/folder in this folder.
After keeping your all projects files. Again open Git GUI/Bash in the current folder.
Then type these as usual: a.git add --all b. git commit -m "Your Desired Heart Sound" c. git push -u origin master.
Finally after following these steps you push your projects to Bitbucket
Error:-fatal: Not a git repository (or any of the parent directories):

Thanks.

Share
Improve this answer
Follow
answered Feb 22, 2022 at 7:40
Naffy Kausar's user avatar
Naffy Kausar
8122 gold badges22 silver badges99 bronze badges
Add a comment

0


Firstly remote verbose with the following command:

git remote -v
And see the result of something like that:

origin  https://github.com/MahfuzKhandaker/StudyOnline.git (fetch)
origin  https://github.com/MahfuzKhandaker/StudyOnline.git (push)
Then you have to run the following command to remove origin:

git remote remove origin
And finally you have to add origin:

git remote  add origin  https://github.com/MahfuzKhandaker/StudyOnline.git
Then run the command:

git branch -M main
git push -u origin main
Hope this helps!

Share
Improve this answer
Follow
answered Oct 11, 2022 at 17:41
Mahfuz Khandaker's user avatar
Mahfuz Khandaker
41455 silver badges1111 bronze badges
Add a comment

0


You can see the multiple ways to solve but I recommended to trying this first. It works for me perfectly.

    step 1. git remote -v 
    step 2. git remote rm origin
    step 3. git add .
    step 4. git commit -m "your commit"
    step 5. git remote set-url origin https://github.com/<your_github_username>/<repository_name>.git
    step 6. git push --set-upstream -f origin main
Note: if error: No such remote 'origin' this error occurred. then before step 5 use this command -

git remote add origin https://github.com/<your_github_username>/<repository_name>.git
then again start from step 5

Follow this 6 steps, Thanks.

Share
Improve this answer
Follow
edited Mar 18 at 17:20
answered Mar 8 at 16:59
Md Wahiduzzaman Emon's user avatar
Md Wahiduzzaman Emon
59133 silver badges1010 bronze badges
Add a comment

0


you just need add github.com to your host file:

ssh-keygen -f "/home/<user>/.ssh/known_hosts" -R "github.com"
Share
Improve this answer
Follow
answered May 3 at 8:37
Jaber Alshami's user avatar
Jaber Alshami
33633 silver badges1414 bronze badges
Add a comment

-4


Sometimes you don't have a local REF for pushing that branch back to the origin.
Try

git push origin master:master
This explicitly indicates which branch to push to (and from)

Share
Improve this answer
Follow
answered Dec 13, 2018 at 13:25
vsriram92's user avatar
vsriram92
51811 gold badge44 silver badges1515 bronze badges
Add a comment
Highly active question. Earn 10 reputation (not counting the association bonus) in order to answer this question. The reputation requirement helps protect this question from spam and non-answer activity.

Not the answer you're looking for? Browse other questions tagged gitgithubversion-controlbranch or ask your own question.
The Overflow Blog
How to use marketing techniques to build a better resume
How the creator of Angular is dehydrating the web (Ep. 574)
Featured on Meta
AI/ML Tool examples part 3 - Title-Drafting Assistant
We are graduating the updated button styling for vote arrows
Temporary policy: ChatGPT is banned
Stack Overflow will be testing a title-drafting assistant, and we’d like your...
We are graduating the "Related questions using Machine Learning" experiment
The [connect] tag is being burninated
Linked
762
Updates were rejected because the tip of your current branch is behind its remote counterpart
2
Push on GIT and Bitbucket
0
Git - 'origin' does not appear to be a git repository
2
fatal: '~peterI/public_html/public.git' does not appear to be a git repository fatal: Could not read from remote repository
1
Local repository is not able to pull branch from remote repository
0
Change Git Username to Connect to My Remote Repo
2
Trying to pull from github i get error remote: Repository not found
1
I'm trying to do a git fetch. However, I'm receiving an error "remote: Repository not found. fatal: repository not found
0
error: failed to push some refs to 'git@github.com:MyGitHub/foo.git'
0
My project files are not getting pushed to GitHub repository
See more linked questions
Related
27
Git push origin master returns "fatal: No path specified."
0
Fatal error on git push origin master?
92
Git push error: "origin does not appear to be a git repository"
129
fatal: 'origin' does not appear to be a git repository
4
GIT: fatal: Could not read from remote repository when you create new branch
0
fatal: Could not read from remote repository error while git push
6
Git push origin Permission to * denied fatal: Could not read from remote repository
14
fatal- 'origin' does not appear to be a git repository
0
Git push origin master -f : "fatal 'origin' does not appear to be a git repository - fatal Could not read from remote repository."
1
Git push results in "Could not read from remote repository"
Hot Network Questions
Dovecot:/Thunderbird sslv3 alert certificate expired: SSL alert number 45
Should I pre-emptively confess after submitting work that was partially generated by ChatGPT?
What is \DocumentMetadata? What key-value pairs does it take and when should I use it?
How far apart has the sun drifted from Alpha Centari due to the expansion of the universe since its formation?
The Planet of the Ants: Giant Ant Physiology
Placing multiple nodes around a circle
Company wants to see offer letter received from another company to match salary
"Solvitas perambulum": Is this real Latin?
How many sorting networks?
What would be an example of something digital which isn't electronic?
Why did it take so long to invent telescopes given glass was used 4000 years ago in Mesopotamia?
Resultant of two polynomials
Why is Killiniq island divided between Nunavut and Labrador?
How can a passenger have opened an emergency exit on an Airbus A321 in flight?
Why did Trinity not take Neo to Morpheus when meeting him in the club?
How change the data arrangement in a list?
Is it appropriate to cite vulgar websites used for gathering data?
Did Nelson Mandela read The Economist in prison?
Can you pack these tetracubes to form a rectangular block with at least one odd side length?
Need help figuring out circuit board design
How to handle it if one player wants to take a risky course of action that nobody else wants?
Is there anything important to know about flying at ~9000ft for the first time?
Demarcated "Proof Idea"
Is Russian the most diverged Slavic language?
 Question feed

STACK OVERFLOW
Questions
Help
PRODUCTS
Teams
Advertising
Collectives
Talent
COMPANY
About
Press
Work Here
Legal
Privacy Policy
Terms of Service
Contact Us
Cookie Settings
Cookie Policy
STACK EXCHANGE NETWORK
Technology
Culture & recreation
Life & arts
Science
Professional
Business
API
DataHowever, at some point, I created a new branch locally called add-calendar-model in case next steps of the app development would go south...

... which is exactly what happened.

However, despite many attempts, I did not manage to get the initial code — i.e. the code from before I created the new branch — from the master branch to my local repository.

So, I decided to manually delete all the files from my local repository and git clone my master branch from GitHub.

This way, I got all my files back, but now, I cannot push any more to the remote repository.

Any time I try to run git push origin add-calendar-model or git push origin master, I get the following error:

fatal: 'origin' does not appear to be a git repository
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
I am not very comfortable with Git and GitHub, as you may have guessed by now, and I have to admit that I have no clue about how to fix this.

Any idea?

gitgithubversion-controlbranch
Share
Improve this question
Follow
asked Aug 27, 2015 at 0:03
Thibaud Clement's user avatar
Thibaud Clement
6,5271010 gold badges5050 silver badges103103 bronze badges
2
I had a similar error, But my problem was I had initialized git in the parent directory of the current folder I was trying it. Just in case if anyone is still facing, can look where the git is initialized and then try again. – 
Himanshu Kriplani
 Apr 17, 2020 at 2:39
Add a comment
17 Answers
Sorted by:

Highest score (default)

321


First, check that your origin is set by running

git remote -v
This should show you all of the push / fetch remotes for the project.

If this returns with no output, skip to last code block.

Verify remote name / address

If this returns showing that you have remotes set, check that the name of the remote matches the remote you are using in your commands.

$git remote -v
myOrigin ssh://git@example.com:1234/myRepo.git (fetch)
myOrigin ssh://git@example.com:1234/myRepo.git (push)

# this will fail because `origin` is not set
$git push origin main

# you need to use
$git push myOrigin main
If you want to rename the remote or change the remote's URL, you'll want to first remove the old remote, and then add the correct one.

Remove the old remote

$git remote remove myOrigin
Add missing remote

You can then add in the proper remote using

$git remote add origin ssh://git@example.com:1234/myRepo.git

# this will now work as expected
$git push origin main
Share
Improve this answer
Follow
edited Nov 4, 2021 at 20:14
Simo Pelle's user avatar
Simo Pelle
14111 silver badge1010 bronze badges
answered Aug 27, 2015 at 0:06
Matt Clark's user avatar
Matt Clark
27.6k1919 gold badges6767 silver badges122122 bronze badges
It worked for me without the ssh:// in front of git@example.com:1234/myRepo.git – 
Carol-Theodor Pelu
 Jul 16, 2018 at 7:05
I was reading this question if you could help with the new repository push error as well? – 
StaticVariable
 Sep 3, 2018 at 7:04
I renamed my remote branch from upstream to origin and it caused the error, after completely deleting the remote reference using git remote remove origin and then adding it again using git remote add origin <url> then it worked fine – 
Uriahs Victor
 Jun 29, 2021 at 18:31
This worked for me, with a slight tweak. git remote -v was showing that my origin was git@bitbucket.org/[repo].git. After removing that origin, I replaced it with just bitbucket.org/[repo].git, and this worked. To clarify, I got rid of the "git@" and just put in the repo URL without a user, prompting it to ask for a user for all push/pull commands (which is what I needed anyway). – 
Bad Programmer
 Aug 3, 2022 at 17:59
Add a comment

31


It works for me.

git remote add origin https://github.com/repo.git
git push origin master
add the repository URL to the origin in the local working directory

Share
Improve this answer
Follow
answered Jul 21, 2020 at 8:22
vinod's user avatar
vinod
52555 silver badges1010 bronze badges
2
When I removed the *.git in the end it worked for me: git remote add origin https://github.com/user/repo – 
Joel Wiklund
 Nov 5, 2022 at 7:12
Add a comment

16


As Matt Clark stated above

However, origin might not be set, so skip the deleting step and simply attempting to add can clear this up.

git remote add origin <"clone">
Where "clone" is simply going into your GitHub repo and copying the "HTTPS clone URL" and pasting into GitBash

Share
Improve this answer
Follow
answered Sep 21, 2015 at 16:38
heb-NR's user avatar
heb-NR
31755 silver badges1313 bronze badges
Add a comment

11


This is the way I updated the master branch

This kind of error occurs commonly after deleting the initial code on your project

So, go ahead, first of all, verify the actual remote version, then remove the origin add the comment, and copy the repo URL into the project files.

$ git remote -v
$ git remote rm origin
$ git commit -m "your commit"
$ git remote add origin https://github.com/user/repo.git
$ git push -f origin master
Share
Improve this answer
Follow
edited Dec 13, 2020 at 23:54
answered Jul 6, 2020 at 16:12
Jose Antonio's user avatar
Jose Antonio
8251414 silver badges2525 bronze badges
1
Try adding explanations to your answer in a way that addresses the question and attempts to help a reader understand. Currently, it just reads like some anecdote and wouldn't even work in the general case (e.g. https://github.com/ is the website root and a git repo) – 
Kache
 Jul 7, 2020 at 5:38
Add a comment

5


if you add your remote repository by using git clone then follow the steps:-

git clone <repo_url> then

git init

git add * *means add all files

git commit -m 'your commit'

git remote -v for check any branch run or not if not then nothing show then we add or fetch the repository. "fetch first". You need to run git pull origin <branch> or git pull -r origin <branch> before a next push.

then

git remote add origin <git url>
 git pull -r origin master
git push -u origin master```
Share
Improve this answer
Follow
answered May 13, 2020 at 11:49
md sha's user avatar
md sha
5111 silver badge11 bronze badge
Add a comment

3


Make sure the config file at .git is correct...Check URL & Make sure your using the correct protocol for your keys ...ProjectWorkspace/.git/config

  ~Wrong url for git@bitbucket
[core]
    repositoryformatversion = 0
    filemode = true
    bare = false
    logallrefupdates = true
[remote "origin"]
    url = gitbucket.org:Prezyack/project-one-hello.git
    fetch = +refs/heads/*:refs/remotes/origin/*

 ~Wrong URL for SSH...
[core]
    repositoryformatversion = 0
    filemode = true
    bare = false
    logallrefupdates = true
    ignorecase = true
    precomposeunicode = true
[remote "origin"]
    fetch = +refs/heads/*:refs/remotes/origin/*
    url = https://emmap1@bitbucket.org/emmap1/bitbucketspacestation.git
[branch "master"]
    remote = origin
    merge = refs/heads/master
We are looking at the URL... e.g: For bitbucket, expect git@bitbucket.org....If its gitbucket.org. make the necessary changes.. SAVE Try pushing again.

Share
Improve this answer
Follow
answered Jul 29, 2016 at 12:32
Magere's user avatar
Magere
9966 bronze badges
Add a comment

2


These two steps worked for me!

Step 1:

git remote set-url origin https://github.com/username/example_repo.git
Step 2:

git push --set-upstream -f origin main
Step 3:

your username and password for github

On step 2, -f is actually required because of the rebase, quote from this post.

Share
Improve this answer
Follow
answered Jan 21, 2021 at 13:07
BlueJapan's user avatar
BlueJapan
1,18622 gold badges1313 silver badges1616 bronze badges
Add a comment

2


For me it helps just by removing existing origin (after i created a new repo and few steps). But before check if the origin is exist in your case:

git remote -v
Then check name of origin (usually set by default) and remove it.

git remote remove origin
And use common github commands while pushing repository to add new origin and finally push your code:

git remote add origin https://github.com/username/repository.git
git branch -M main

git push -u origin main
Share
Improve this answer
Follow
edited Oct 17, 2022 at 8:09
answered Aug 5, 2022 at 9:40
user15038732
Add a comment

1


A similar error appears while pulling the changes from the origin. If you are trying in Intellij from the menu options, the pull might not work directly.

Go to terminal and type this command and this should work out: git pull origin master

Share
Improve this answer
Follow
answered Jun 13, 2018 at 7:50
Nikhil Shrivastav's user avatar
Nikhil Shrivastav
7111 silver badge22 bronze badges
Add a comment

1


What fixed this for me was re-setting my origin url:

git remote set-url origin https://github.com/username/example_repo.git

And then I was able to successfully git push my project. I had to do this even though when I viewed my origins with git remote -v, that the urls were same as what I re-set it as.

Share
Improve this answer
Follow
answered Nov 13, 2020 at 4:27
deesolie's user avatar
deesolie
81766 silver badges1717 bronze badges
Add a comment

1


Most probably the issue is that your remote origin is not set.

git add .
git commit -m "Your commit message"
git remote add origin https://repositoryurlpath.git
git push origin master
Extra Tips:

Check if the remote origin is set

git remote -v
Reset the remote origin

git remote remove origin
git remote add origin https://repositoryurlpath.git
Share
Improve this answer
Follow
answered Sep 14, 2021 at 19:26
Erielama's user avatar
Erielama
11111 silver badge33 bronze badges
Add a comment

0


I had the same issue. When I checked my config file I noticed that 'fetch = +refs/heads/:refs/remotes/origin/' was on the same line as 'url = Z:/GIT/REPOS/SEL.git' as shown:

[core]
    repositoryformatversion = 0
    filemode = false
    bare = false
    logallrefupdates = true
    symlinks = false
    ignorecase = true
[remote "origin"]
    url = Z:/GIT/REPOS/SEL.git     fetch = +refs/heads/*:refs/remotes/origin/*
[branch "master"]
    remote = origin
    merge = refs/heads/master
[gui]
    wmstate = normal
    geometry = 1109x563+32+32 216 255
At first I did not think that this would have mattered but after seeing the post by Magere I moved the line and that fixed the problem:

[core]
    repositoryformatversion = 0
    filemode = false
    bare = false
    logallrefupdates = true
    symlinks = false
    ignorecase = true
[remote "origin"]
    url = Z:/GIT/REPOS/SEL.git
    fetch = +refs/heads/*:refs/remotes/origin/*
[branch "master"]
    remote = origin
    merge = refs/heads/master
[gui]
    wmstate = normal
    geometry = 1109x563+32+32 216 255
Share
Improve this answer
Follow
answered Nov 21, 2019 at 21:05
Beaug45's user avatar
Beaug45
111 bronze badge
Add a comment

0


It happens when you push your code from the current location but after cloning any projects Git creates its own different folder so we have to change our current directory to the required directory. If any got these issue. We can solve it by following these easy steps:-

Firstly create an empty folder.
Open Git GUI/Bash or CMD in the empty folder. Open the empty folder and right click and then open Git.
Click on a clone in Bitbucket(after creating your repository) and copy the cloning path of your repository.
Paste it into your Git and Enter.
After cloning, a new folder is created by git.
Change your directory to the new folder that is created by Git after cloning your repository.
Paste/puts your desired projects/files/folder in this folder.
After keeping your all projects files. Again open Git GUI/Bash in the current folder.
Then type these as usual: a.git add --all b. git commit -m "Your Desired Heart Sound" c. git push -u origin master.
Finally after following these steps you push your projects to Bitbucket
Error:-fatal: Not a git repository (or any of the parent directories):

Thanks.

Share
Improve this answer
Follow
answered Feb 22, 2022 at 7:40
Naffy Kausar's user avatar
Naffy Kausar
8122 gold badges22 silver badges99 bronze badges
Add a comment

0


Firstly remote verbose with the following command:

git remote -v
And see the result of something like that:

origin  https://github.com/MahfuzKhandaker/StudyOnline.git (fetch)
origin  https://github.com/MahfuzKhandaker/StudyOnline.git (push)
Then you have to run the following command to remove origin:

git remote remove origin
And finally you have to add origin:

git remote  add origin  https://github.com/MahfuzKhandaker/StudyOnline.git
Then run the command:

git branch -M main
git push -u origin main
Hope this helps!

Share
Improve this answer
Follow
answered Oct 11, 2022 at 17:41
Mahfuz Khandaker's user avatar
Mahfuz Khandaker
41455 silver badges1111 bronze badges
Add a comment

0


You can see the multiple ways to solve but I recommended to trying this first. It works for me perfectly.

    step 1. git remote -v 
    step 2. git remote rm origin
    step 3. git add .
    step 4. git commit -m "your commit"
    step 5. git remote set-url origin https://github.com/<your_github_username>/<repository_name>.git
    step 6. git push --set-upstream -f origin main
Note: if error: No such remote 'origin' this error occurred. then before step 5 use this command -

git remote add origin https://github.com/<your_github_username>/<repository_name>.git
then again start from step 5

Follow this 6 steps, Thanks.

Share
Improve this answer
Follow
edited Mar 18 at 17:20
answered Mar 8 at 16:59
Md Wahiduzzaman Emon's user avatar
Md Wahiduzzaman Emon
59133 silver badges1010 bronze badges
Add a comment

0


you just need add github.com to your host file:

ssh-keygen -f "/home/<user>/.ssh/known_hosts" -R "github.com"
Share
Improve this answer
Follow
answered May 3 at 8:37
Jaber Alshami's user avatar
Jaber Alshami
33633 silver badges1414 bronze badges
Add a comment

-4


Sometimes you don't have a local REF for pushing that branch back to the origin.
Try

git push origin master:master
This explicitly indicates which branch to push to (and from)

Share
Improve this answer
Follow
answered Dec 13, 2018 at 13:25
vsriram92's user avatar
vsriram92
51811 gold badge44 silver badges1515 bronze badges
Add a comment
Highly active question. Earn 10 reputation (not counting the association bonus) in order to answer this question. The reputation requirement helps protect this question from spam and non-answer activity.

Not the answer you're looking for? Browse other questions tagged gitgithubversion-controlbranch or ask your own question.
The Overflow Blog
How to use marketing techniques to build a better resume
How the creator of Angular is dehydrating the web (Ep. 574)
Featured on Meta
AI/ML Tool examples part 3 - Title-Drafting Assistant
We are graduating the updated button styling for vote arrows
Temporary policy: ChatGPT is banned
Stack Overflow will be testing a title-drafting assistant, and we’d like your...
We are graduating the "Related questions using Machine Learning" experiment
The [connect] tag is being burninated
Linked
762
Updates were rejected because the tip of your current branch is behind its remote counterpart
2
Push on GIT and Bitbucket
0
Git - 'origin' does not appear to be a git repository
2
fatal: '~peterI/public_html/public.git' does not appear to be a git repository fatal: Could not read from remote repository
1
Local repository is not able to pull branch from remote repository
0
Change Git Username to Connect to My Remote Repo
2
Trying to pull from github i get error remote: Repository not found
1
I'm trying to do a git fetch. However, I'm receiving an error "remote: Repository not found. fatal: repository not found
0
error: failed to push some refs to 'git@github.com:MyGitHub/foo.git'
0
My project files are not getting pushed to GitHub repository
See more linked questions
Related
27
Git push origin master returns "fatal: No path specified."
0
Fatal error on git push origin master?
92
Git push error: "origin does not appear to be a git repository"
129
fatal: 'origin' does not appear to be a git repository
4
GIT: fatal: Could not read from remote repository when you create new branch
0
fatal: Could not read from remote repository error while git push
6
Git push origin Permission to * denied fatal: Could not read from remote repository
14
fatal- 'origin' does not appear to be a git repository
0
Git push origin master -f : "fatal 'origin' does not appear to be a git repository - fatal Could not read from remote repository."
1
Git push results in "Could not read from remote repository"
Hot Network Questions
Dovecot:/Thunderbird sslv3 alert certificate expired: SSL alert number 45
Should I pre-emptively confess after submitting work that was partially generated by ChatGPT?
What is \DocumentMetadata? What key-value pairs does it take and when should I use it?
How far apart has the sun drifted from Alpha Centari due to the expansion of the universe since its formation?
The Planet of the Ants: Giant Ant Physiology
Placing multiple nodes around a circle
Company wants to see offer letter received from another company to match salary
"Solvitas perambulum": Is this real Latin?
How many sorting networks?
What would be an example of something digital which isn't electronic?
Why did it take so long to invent telescopes given glass was used 4000 years ago in Mesopotamia?
Resultant of two polynomials
Why is Killiniq island divided between Nunavut and Labrador?
How can a passenger have opened an emergency exit on an Airbus A321 in flight?
Why did Trinity not take Neo to Morpheus when meeting him in the club?
How change the data arrangement in a list?
Is it appropriate to cite vulgar websites used for gathering data?
Did Nelson Mandela read The Economist in prison?
Can you pack these tetracubes to form a rectangular block with at least one odd side length?
Need help figuring out circuit board design
How to handle it if one player wants to take a risky course of action that nobody else wants?
Is there anything important to know about flying at ~9000ft for the first time?
Demarcated "Proof Idea"
Is Russian the most diverged Slavic language?
 Question feed

STACK OVERFLOW
Questions
Help
PRODUCTS
Teams
Advertising
Collectives
Talent
COMPANY
About
Press
Work Here
Legal
Privacy Policy
Terms of Service
Contact Us
Cookie Settings
Cookie Policy
STACK EXCHANGE NETWORK
Technology
Culture & recreation
Life & arts
Science
Professional
Business
API
DataHowever, at some point, I created a new branch locally called add-calendar-model in case next steps of the app development would go south...

... which is exactly what happened.

However, despite many attempts, I did not manage to get the initial code — i.e. the code from before I created the new branch — from the master branch to my local repository.

So, I decided to manually delete all the files from my local repository and git clone my master branch from GitHub.

This way, I got all my files back, but now, I cannot push any more to the remote repository.

Any time I try to run git push origin add-calendar-model or git push origin master, I get the following error:

fatal: 'origin' does not appear to be a git repository
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
I am not very comfortable with Git and GitHub, as you may have guessed by now, and I have to admit that I have no clue about how to fix this.

Any idea?

gitgithubversion-controlbranch
Share
Improve this question
Follow
asked Aug 27, 2015 at 0:03
Thibaud Clement's user avatar
Thibaud Clement
6,5271010 gold badges5050 silver badges103103 bronze badges
2
I had a similar error, But my problem was I had initialized git in the parent directory of the current folder I was trying it. Just in case if anyone is still facing, can look where the git is initialized and then try again. – 
Himanshu Kriplani
 Apr 17, 2020 at 2:39
Add a comment
17 Answers
Sorted by:

Highest score (default)

321


First, check that your origin is set by running

git remote -v
This should show you all of the push / fetch remotes for the project.

If this returns with no output, skip to last code block.

Verify remote name / address

If this returns showing that you have remotes set, check that the name of the remote matches the remote you are using in your commands.

$git remote -v
myOrigin ssh://git@example.com:1234/myRepo.git (fetch)
myOrigin ssh://git@example.com:1234/myRepo.git (push)

# this will fail because `origin` is not set
$git push origin main

# you need to use
$git push myOrigin main
If you want to rename the remote or change the remote's URL, you'll want to first remove the old remote, and then add the correct one.

Remove the old remote

$git remote remove myOrigin
Add missing remote

You can then add in the proper remote using

$git remote add origin ssh://git@example.com:1234/myRepo.git

# this will now work as expected
$git push origin main
Share
Improve this answer
Follow
edited Nov 4, 2021 at 20:14
Simo Pelle's user avatar
Simo Pelle
14111 silver badge1010 bronze badges
answered Aug 27, 2015 at 0:06
Matt Clark's user avatar
Matt Clark
27.6k1919 gold badges6767 silver badges122122 bronze badges
It worked for me without the ssh:// in front of git@example.com:1234/myRepo.git – 
Carol-Theodor Pelu
 Jul 16, 2018 at 7:05
I was reading this question if you could help with the new repository push error as well? – 
StaticVariable
 Sep 3, 2018 at 7:04
I renamed my remote branch from upstream to origin and it caused the error, after completely deleting the remote reference using git remote remove origin and then adding it again using git remote add origin <url> then it worked fine – 
Uriahs Victor
 Jun 29, 2021 at 18:31
This worked for me, with a slight tweak. git remote -v was showing that my origin was git@bitbucket.org/[repo].git. After removing that origin, I replaced it with just bitbucket.org/[repo].git, and this worked. To clarify, I got rid of the "git@" and just put in the repo URL without a user, prompting it to ask for a user for all push/pull commands (which is what I needed anyway). – 
Bad Programmer
 Aug 3, 2022 at 17:59
Add a comment

31


It works for me.

git remote add origin https://github.com/repo.git
git push origin master
add the repository URL to the origin in the local working directory

Share
Improve this answer
Follow
answered Jul 21, 2020 at 8:22
vinod's user avatar
vinod
52555 silver badges1010 bronze badges
2
When I removed the *.git in the end it worked for me: git remote add origin https://github.com/user/repo – 
Joel Wiklund
 Nov 5, 2022 at 7:12
Add a comment

16


As Matt Clark stated above

However, origin might not be set, so skip the deleting step and simply attempting to add can clear this up.

git remote add origin <"clone">
Where "clone" is simply going into your GitHub repo and copying the "HTTPS clone URL" and pasting into GitBash

Share
Improve this answer
Follow
answered Sep 21, 2015 at 16:38
heb-NR's user avatar
heb-NR
31755 silver badges1313 bronze badges
Add a comment

11


This is the way I updated the master branch

This kind of error occurs commonly after deleting the initial code on your project

So, go ahead, first of all, verify the actual remote version, then remove the origin add the comment, and copy the repo URL into the project files.

$ git remote -v
$ git remote rm origin
$ git commit -m "your commit"
$ git remote add origin https://github.com/user/repo.git
$ git push -f origin master
Share
Improve this answer
Follow
edited Dec 13, 2020 at 23:54
answered Jul 6, 2020 at 16:12
Jose Antonio's user avatar
Jose Antonio
8251414 silver badges2525 bronze badges
1
Try adding explanations to your answer in a way that addresses the question and attempts to help a reader understand. Currently, it just reads like some anecdote and wouldn't even work in the general case (e.g. https://github.com/ is the website root and a git repo) – 
Kache
 Jul 7, 2020 at 5:38
Add a comment

5


if you add your remote repository by using git clone then follow the steps:-

git clone <repo_url> then

git init

git add * *means add all files

git commit -m 'your commit'

git remote -v for check any branch run or not if not then nothing show then we add or fetch the repository. "fetch first". You need to run git pull origin <branch> or git pull -r origin <branch> before a next push.

then

git remote add origin <git url>
 git pull -r origin master
git push -u origin master```
Share
Improve this answer
Follow
answered May 13, 2020 at 11:49
md sha's user avatar
md sha
5111 silver badge11 bronze badge
Add a comment

3


Make sure the config file at .git is correct...Check URL & Make sure your using the correct protocol for your keys ...ProjectWorkspace/.git/config

  ~Wrong url for git@bitbucket
[core]
    repositoryformatversion = 0
    filemode = true
    bare = false
    logallrefupdates = true
[remote "origin"]
    url = gitbucket.org:Prezyack/project-one-hello.git
    fetch = +refs/heads/*:refs/remotes/origin/*

 ~Wrong URL for SSH...
[core]
    repositoryformatversion = 0
    filemode = true
    bare = false
    logallrefupdates = true
    ignorecase = true
    precomposeunicode = true
[remote "origin"]
    fetch = +refs/heads/*:refs/remotes/origin/*
    url = https://emmap1@bitbucket.org/emmap1/bitbucketspacestation.git
[branch "master"]
    remote = origin
    merge = refs/heads/master
We are looking at the URL... e.g: For bitbucket, expect git@bitbucket.org....If its gitbucket.org. make the necessary changes.. SAVE Try pushing again.

Share
Improve this answer
Follow
answered Jul 29, 2016 at 12:32
Magere's user avatar
Magere
9966 bronze badges
Add a comment

2


These two steps worked for me!

Step 1:

git remote set-url origin https://github.com/username/example_repo.git
Step 2:

git push --set-upstream -f origin main
Step 3:

your username and password for github

On step 2, -f is actually required because of the rebase, quote from this post.

Share
Improve this answer
Follow
answered Jan 21, 2021 at 13:07
BlueJapan's user avatar
BlueJapan
1,18622 gold badges1313 silver badges1616 bronze badges
Add a comment

2


For me it helps just by removing existing origin (after i created a new repo and few steps). But before check if the origin is exist in your case:

git remote -v
Then check name of origin (usually set by default) and remove it.

git remote remove origin
And use common github commands while pushing repository to add new origin and finally push your code:

git remote add origin https://github.com/username/repository.git
git branch -M main

git push -u origin main
Share
Improve this answer
Follow
edited Oct 17, 2022 at 8:09
answered Aug 5, 2022 at 9:40
user15038732
Add a comment

1


A similar error appears while pulling the changes from the origin. If you are trying in Intellij from the menu options, the pull might not work directly.

Go to terminal and type this command and this should work out: git pull origin master

Share
Improve this answer
Follow
answered Jun 13, 2018 at 7:50
Nikhil Shrivastav's user avatar
Nikhil Shrivastav
7111 silver badge22 bronze badges
Add a comment

1


What fixed this for me was re-setting my origin url:

git remote set-url origin https://github.com/username/example_repo.git

And then I was able to successfully git push my project. I had to do this even though when I viewed my origins with git remote -v, that the urls were same as what I re-set it as.

Share
Improve this answer
Follow
answered Nov 13, 2020 at 4:27
deesolie's user avatar
deesolie
81766 silver badges1717 bronze badges
Add a comment

1


Most probably the issue is that your remote origin is not set.

git add .
git commit -m "Your commit message"
git remote add origin https://repositoryurlpath.git
git push origin master
Extra Tips:

Check if the remote origin is set

git remote -v
Reset the remote origin

git remote remove origin
git remote add origin https://repositoryurlpath.git
Share
Improve this answer
Follow
answered Sep 14, 2021 at 19:26
Erielama's user avatar
Erielama
11111 silver badge33 bronze badges
Add a comment

0


I had the same issue. When I checked my config file I noticed that 'fetch = +refs/heads/:refs/remotes/origin/' was on the same line as 'url = Z:/GIT/REPOS/SEL.git' as shown:

[core]
    repositoryformatversion = 0
    filemode = false
    bare = false
    logallrefupdates = true
    symlinks = false
    ignorecase = true
[remote "origin"]
    url = Z:/GIT/REPOS/SEL.git     fetch = +refs/heads/*:refs/remotes/origin/*
[branch "master"]
    remote = origin
    merge = refs/heads/master
[gui]
    wmstate = normal
    geometry = 1109x563+32+32 216 255
At first I did not think that this would have mattered but after seeing the post by Magere I moved the line and that fixed the problem:

[core]
    repositoryformatversion = 0
    filemode = false
    bare = false
    logallrefupdates = true
    symlinks = false
    ignorecase = true
[remote "origin"]
    url = Z:/GIT/REPOS/SEL.git
    fetch = +refs/heads/*:refs/remotes/origin/*
[branch "master"]
    remote = origin
    merge = refs/heads/master
[gui]
    wmstate = normal
    geometry = 1109x563+32+32 216 255
Share
Improve this answer
Follow
answered Nov 21, 2019 at 21:05
Beaug45's user avatar
Beaug45
111 bronze badge
Add a comment

0


It happens when you push your code from the current location but after cloning any projects Git creates its own different folder so we have to change our current directory to the required directory. If any got these issue. We can solve it by following these easy steps:-

Firstly create an empty folder.
Open Git GUI/Bash or CMD in the empty folder. Open the empty folder and right click and then open Git.
Click on a clone in Bitbucket(after creating your repository) and copy the cloning path of your repository.
Paste it into your Git and Enter.
After cloning, a new folder is created by git.
Change your directory to the new folder that is created by Git after cloning your repository.
Paste/puts your desired projects/files/folder in this folder.
After keeping your all projects files. Again open Git GUI/Bash in the current folder.
Then type these as usual: a.git add --all b. git commit -m "Your Desired Heart Sound" c. git push -u origin master.
Finally after following these steps you push your projects to Bitbucket
Error:-fatal: Not a git repository (or any of the parent directories):

Thanks.

Share
Improve this answer
Follow
answered Feb 22, 2022 at 7:40
Naffy Kausar's user avatar
Naffy Kausar
8122 gold badges22 silver badges99 bronze badges
Add a comment

0


Firstly remote verbose with the following command:

git remote -v
And see the result of something like that:

origin  https://github.com/MahfuzKhandaker/StudyOnline.git (fetch)
origin  https://github.com/MahfuzKhandaker/StudyOnline.git (push)
Then you have to run the following command to remove origin:

git remote remove origin
And finally you have to add origin:

git remote  add origin  https://github.com/MahfuzKhandaker/StudyOnline.git
Then run the command:

git branch -M main
git push -u origin main
Hope this helps!

Share
Improve this answer
Follow
answered Oct 11, 2022 at 17:41
Mahfuz Khandaker's user avatar
Mahfuz Khandaker
41455 silver badges1111 bronze badges
Add a comment

0


You can see the multiple ways to solve but I recommended to trying this first. It works for me perfectly.

    step 1. git remote -v 
    step 2. git remote rm origin
    step 3. git add .
    step 4. git commit -m "your commit"
    step 5. git remote set-url origin https://github.com/<your_github_username>/<repository_name>.git
    step 6. git push --set-upstream -f origin main
Note: if error: No such remote 'origin' this error occurred. then before step 5 use this command -

git remote add origin https://github.com/<your_github_username>/<repository_name>.git
then again start from step 5

Follow this 6 steps, Thanks.

Share
Improve this answer
Follow
edited Mar 18 at 17:20
answered Mar 8 at 16:59
Md Wahiduzzaman Emon's user avatar
Md Wahiduzzaman Emon
59133 silver badges1010 bronze badges
Add a comment

0


you just need add github.com to your host file:

ssh-keygen -f "/home/<user>/.ssh/known_hosts" -R "github.com"
Share
Improve this answer
Follow
answered May 3 at 8:37
Jaber Alshami's user avatar
Jaber Alshami
33633 silver badges1414 bronze badges
Add a comment

-4


Sometimes you don't have a local REF for pushing that branch back to the origin.
Try

git push origin master:master
This explicitly indicates which branch to push to (and from)

Share
Improve this answer
Follow
answered Dec 13, 2018 at 13:25
vsriram92's user avatar
vsriram92
51811 gold badge44 silver badges1515 bronze badges
Add a comment
Highly active question. Earn 10 reputation (not counting the association bonus) in order to answer this question. The reputation requirement helps protect this question from spam and non-answer activity.

Not the answer you're looking for? Browse other questions tagged gitgithubversion-controlbranch or ask your own question.
The Overflow Blog
How to use marketing techniques to build a better resume
How the creator of Angular is dehydrating the web (Ep. 574)
Featured on Meta
AI/ML Tool examples part 3 - Title-Drafting Assistant
We are graduating the updated button styling for vote arrows
Temporary policy: ChatGPT is banned
Stack Overflow will be testing a title-drafting assistant, and we’d like your...
We are graduating the "Related questions using Machine Learning" experiment
The [connect] tag is being burninated
Linked
762
Updates were rejected because the tip of your current branch is behind its remote counterpart
2
Push on GIT and Bitbucket
0
Git - 'origin' does not appear to be a git repository
2
fatal: '~peterI/public_html/public.git' does not appear to be a git repository fatal: Could not read from remote repository
1
Local repository is not able to pull branch from remote repository
0
Change Git Username to Connect to My Remote Repo
2
Trying to pull from github i get error remote: Repository not found
1
I'm trying to do a git fetch. However, I'm receiving an error "remote: Repository not found. fatal: repository not found
0
error: failed to push some refs to 'git@github.com:MyGitHub/foo.git'
0
My project files are not getting pushed to GitHub repository
See more linked questions
Related
27
Git push origin master returns "fatal: No path specified."
0
Fatal error on git push origin master?
92
Git push error: "origin does not appear to be a git repository"
129
fatal: 'origin' does not appear to be a git repository
4
GIT: fatal: Could not read from remote repository when you create new branch
0
fatal: Could not read from remote repository error while git push
6
Git push origin Permission to * denied fatal: Could not read from remote repository
14
fatal- 'origin' does not appear to be a git repository
0
Git push origin master -f : "fatal 'origin' does not appear to be a git repository - fatal Could not read from remote repository."
1
Git push results in "Could not read from remote repository"
Hot Network Questions
Dovecot:/Thunderbird sslv3 alert certificate expired: SSL alert number 45
Should I pre-emptively confess after submitting work that was partially generated by ChatGPT?
What is \DocumentMetadata? What key-value pairs does it take and when should I use it?
How far apart has the sun drifted from Alpha Centari due to the expansion of the universe since its formation?
The Planet of the Ants: Giant Ant Physiology
Placing multiple nodes around a circle
Company wants to see offer letter received from another company to match salary
"Solvitas perambulum": Is this real Latin?
How many sorting networks?
What would be an example of something digital which isn't electronic?
Why did it take so long to invent telescopes given glass was used 4000 years ago in Mesopotamia?
Resultant of two polynomials
Why is Killiniq island divided between Nunavut and Labrador?
How can a passenger have opened an emergency exit on an Airbus A321 in flight?
Why did Trinity not take Neo to Morpheus when meeting him in the club?
How change the data arrangement in a list?
Is it appropriate to cite vulgar websites used for gathering data?
Did Nelson Mandela read The Economist in prison?
Can you pack these tetracubes to form a rectangular block with at least one odd side length?
Need help figuring out circuit board design
How to handle it if one player wants to take a risky course of action that nobody else wants?
Is there anything important to know about flying at ~9000ft for the first time?
Demarcated "Proof Idea"
Is Russian the most diverged Slavic language?
 Question feed

STACK OVERFLOW
Questions
Help
PRODUCTS
Teams
Advertising
Collectives
Talent
COMPANY
About
Press
Work Here
Legal
Privacy Policy
Terms of Service
Contact Us
Cookie Settings
Cookie Policy
STACK EXCHANGE NETWORK
Technology
Culture & recreation
Life & arts
Science
Professional
Business
API
DataHowever, at some point, I created a new branch locally called add-calendar-model in case next steps of the app development would go south...

... which is exactly what happened.

However, despite many attempts, I did not manage to get the initial code — i.e. the code from before I created the new branch — from the master branch to my local repository.

So, I decided to manually delete all the files from my local repository and git clone my master branch from GitHub.

This way, I got all my files back, but now, I cannot push any more to the remote repository.

Any time I try to run git push origin add-calendar-model or git push origin master, I get the following error:

fatal: 'origin' does not appear to be a git repository
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
I am not very comfortable with Git and GitHub, as you may have guessed by now, and I have to admit that I have no clue about how to fix this.

Any idea?

gitgithubversion-controlbranch
Share
Improve this question
Follow
asked Aug 27, 2015 at 0:03
Thibaud Clement's user avatar
Thibaud Clement
6,5271010 gold badges5050 silver badges103103 bronze badges
2
I had a similar error, But my problem was I had initialized git in the parent directory of the current folder I was trying it. Just in case if anyone is still facing, can look where the git is initialized and then try again. – 
Himanshu Kriplani
 Apr 17, 2020 at 2:39
Add a comment
17 Answers
Sorted by:

Highest score (default)

321


First, check that your origin is set by running

git remote -v
This should show you all of the push / fetch remotes for the project.

If this returns with no output, skip to last code block.

Verify remote name / address

If this returns showing that you have remotes set, check that the name of the remote matches the remote you are using in your commands.

$git remote -v
myOrigin ssh://git@example.com:1234/myRepo.git (fetch)
myOrigin ssh://git@example.com:1234/myRepo.git (push)

# this will fail because `origin` is not set
$git push origin main

# you need to use
$git push myOrigin main
If you want to rename the remote or change the remote's URL, you'll want to first remove the old remote, and then add the correct one.

Remove the old remote

$git remote remove myOrigin
Add missing remote

You can then add in the proper remote using

$git remote add origin ssh://git@example.com:1234/myRepo.git

# this will now work as expected
$git push origin main
Share
Improve this answer
Follow
edited Nov 4, 2021 at 20:14
Simo Pelle's user avatar
Simo Pelle
14111 silver badge1010 bronze badges
answered Aug 27, 2015 at 0:06
Matt Clark's user avatar
Matt Clark
27.6k1919 gold badges6767 silver badges122122 bronze badges
It worked for me without the ssh:// in front of git@example.com:1234/myRepo.git – 
Carol-Theodor Pelu
 Jul 16, 2018 at 7:05
I was reading this question if you could help with the new repository push error as well? – 
StaticVariable
 Sep 3, 2018 at 7:04
I renamed my remote branch from upstream to origin and it caused the error, after completely deleting the remote reference using git remote remove origin and then adding it again using git remote add origin <url> then it worked fine – 
Uriahs Victor
 Jun 29, 2021 at 18:31
This worked for me, with a slight tweak. git remote -v was showing that my origin was git@bitbucket.org/[repo].git. After removing that origin, I replaced it with just bitbucket.org/[repo].git, and this worked. To clarify, I got rid of the "git@" and just put in the repo URL without a user, prompting it to ask for a user for all push/pull commands (which is what I needed anyway). – 
Bad Programmer
 Aug 3, 2022 at 17:59
Add a comment

31


It works for me.

git remote add origin https://github.com/repo.git
git push origin master
add the repository URL to the origin in the local working directory

Share
Improve this answer
Follow
answered Jul 21, 2020 at 8:22
vinod's user avatar
vinod
52555 silver badges1010 bronze badges
2
When I removed the *.git in the end it worked for me: git remote add origin https://github.com/user/repo – 
Joel Wiklund
 Nov 5, 2022 at 7:12
Add a comment

16


As Matt Clark stated above

However, origin might not be set, so skip the deleting step and simply attempting to add can clear this up.

git remote add origin <"clone">
Where "clone" is simply going into your GitHub repo and copying the "HTTPS clone URL" and pasting into GitBash

Share
Improve this answer
Follow
answered Sep 21, 2015 at 16:38
heb-NR's user avatar
heb-NR
31755 silver badges1313 bronze badges
Add a comment

11


This is the way I updated the master branch

This kind of error occurs commonly after deleting the initial code on your project

So, go ahead, first of all, verify the actual remote version, then remove the origin add the comment, and copy the repo URL into the project files.

$ git remote -v
$ git remote rm origin
$ git commit -m "your commit"
$ git remote add origin https://github.com/user/repo.git
$ git push -f origin master
Share
Improve this answer
Follow
edited Dec 13, 2020 at 23:54
answered Jul 6, 2020 at 16:12
Jose Antonio's user avatar
Jose Antonio
8251414 silver badges2525 bronze badges
1
Try adding explanations to your answer in a way that addresses the question and attempts to help a reader understand. Currently, it just reads like some anecdote and wouldn't even work in the general case (e.g. https://github.com/ is the website root and a git repo) – 
Kache
 Jul 7, 2020 at 5:38
Add a comment

5


if you add your remote repository by using git clone then follow the steps:-

git clone <repo_url> then

git init

git add * *means add all files

git commit -m 'your commit'

git remote -v for check any branch run or not if not then nothing show then we add or fetch the repository. "fetch first". You need to run git pull origin <branch> or git pull -r origin <branch> before a next push.

then

git remote add origin <git url>
 git pull -r origin master
git push -u origin master```
Share
Improve this answer
Follow
answered May 13, 2020 at 11:49
md sha's user avatar
md sha
5111 silver badge11 bronze badge
Add a comment

3


Make sure the config file at .git is correct...Check URL & Make sure your using the correct protocol for your keys ...ProjectWorkspace/.git/config

  ~Wrong url for git@bitbucket
[core]
    repositoryformatversion = 0
    filemode = true
    bare = false
    logallrefupdates = true
[remote "origin"]
    url = gitbucket.org:Prezyack/project-one-hello.git
    fetch = +refs/heads/*:refs/remotes/origin/*

 ~Wrong URL for SSH...
[core]
    repositoryformatversion = 0
    filemode = true
    bare = false
    logallrefupdates = true
    ignorecase = true
    precomposeunicode = true
[remote "origin"]
    fetch = +refs/heads/*:refs/remotes/origin/*
    url = https://emmap1@bitbucket.org/emmap1/bitbucketspacestation.git
[branch "master"]
    remote = origin
    merge = refs/heads/master
We are looking at the URL... e.g: For bitbucket, expect git@bitbucket.org....If its gitbucket.org. make the necessary changes.. SAVE Try pushing again.

Share
Improve this answer
Follow
answered Jul 29, 2016 at 12:32
Magere's user avatar
Magere
9966 bronze badges
Add a comment

2


These two steps worked for me!

Step 1:

git remote set-url origin https://github.com/username/example_repo.git
Step 2:

git push --set-upstream -f origin main
Step 3:

your username and password for github

On step 2, -f is actually required because of the rebase, quote from this post.

Share
Improve this answer
Follow
answered Jan 21, 2021 at 13:07
BlueJapan's user avatar
BlueJapan
1,18622 gold badges1313 silver badges1616 bronze badges
Add a comment

2


For me it helps just by removing existing origin (after i created a new repo and few steps). But before check if the origin is exist in your case:

git remote -v
Then check name of origin (usually set by default) and remove it.

git remote remove origin
And use common github commands while pushing repository to add new origin and finally push your code:

git remote add origin https://github.com/username/repository.git
git branch -M main

git push -u origin main
Share
Improve this answer
Follow
edited Oct 17, 2022 at 8:09
answered Aug 5, 2022 at 9:40
user15038732
Add a comment

1


A similar error appears while pulling the changes from the origin. If you are trying in Intellij from the menu options, the pull might not work directly.

Go to terminal and type this command and this should work out: git pull origin master

Share
Improve this answer
Follow
answered Jun 13, 2018 at 7:50
Nikhil Shrivastav's user avatar
Nikhil Shrivastav
7111 silver badge22 bronze badges
Add a comment

1


What fixed this for me was re-setting my origin url:

git remote set-url origin https://github.com/username/example_repo.git

And then I was able to successfully git push my project. I had to do this even though when I viewed my origins with git remote -v, that the urls were same as what I re-set it as.

Share
Improve this answer
Follow
answered Nov 13, 2020 at 4:27
deesolie's user avatar
deesolie
81766 silver badges1717 bronze badges
Add a comment

1


Most probably the issue is that your remote origin is not set.

git add .
git commit -m "Your commit message"
git remote add origin https://repositoryurlpath.git
git push origin master
Extra Tips:

Check if the remote origin is set

git remote -v
Reset the remote origin

git remote remove origin
git remote add origin https://repositoryurlpath.git
Share
Improve this answer
Follow
answered Sep 14, 2021 at 19:26
Erielama's user avatar
Erielama
11111 silver badge33 bronze badges
Add a comment

0


I had the same issue. When I checked my config file I noticed that 'fetch = +refs/heads/:refs/remotes/origin/' was on the same line as 'url = Z:/GIT/REPOS/SEL.git' as shown:

[core]
    repositoryformatversion = 0
    filemode = false
    bare = false
    logallrefupdates = true
    symlinks = false
    ignorecase = true
[remote "origin"]
    url = Z:/GIT/REPOS/SEL.git     fetch = +refs/heads/*:refs/remotes/origin/*
[branch "master"]
    remote = origin
    merge = refs/heads/master
[gui]
    wmstate = normal
    geometry = 1109x563+32+32 216 255
At first I did not think that this would have mattered but after seeing the post by Magere I moved the line and that fixed the problem:

[core]
    repositoryformatversion = 0
    filemode = false
    bare = false
    logallrefupdates = true
    symlinks = false
    ignorecase = true
[remote "origin"]
    url = Z:/GIT/REPOS/SEL.git
    fetch = +refs/heads/*:refs/remotes/origin/*
[branch "master"]
    remote = origin
    merge = refs/heads/master
[gui]
    wmstate = normal
    geometry = 1109x563+32+32 216 255
Share
Improve this answer
Follow
answered Nov 21, 2019 at 21:05
Beaug45's user avatar
Beaug45
111 bronze badge
Add a comment

0


It happens when you push your code from the current location but after cloning any projects Git creates its own different folder so we have to change our current directory to the required directory. If any got these issue. We can solve it by following these easy steps:-

Firstly create an empty folder.
Open Git GUI/Bash or CMD in the empty folder. Open the empty folder and right click and then open Git.
Click on a clone in Bitbucket(after creating your repository) and copy the cloning path of your repository.
Paste it into your Git and Enter.
After cloning, a new folder is created by git.
Change your directory to the new folder that is created by Git after cloning your repository.
Paste/puts your desired projects/files/folder in this folder.
After keeping your all projects files. Again open Git GUI/Bash in the current folder.
Then type these as usual: a.git add --all b. git commit -m "Your Desired Heart Sound" c. git push -u origin master.
Finally after following these steps you push your projects to Bitbucket
Error:-fatal: Not a git repository (or any of the parent directories):

Thanks.

Share
Improve this answer
Follow
answered Feb 22, 2022 at 7:40
Naffy Kausar's user avatar
Naffy Kausar
8122 gold badges22 silver badges99 bronze badges
Add a comment

0


Firstly remote verbose with the following command:

git remote -v
And see the result of something like that:

origin  https://github.com/MahfuzKhandaker/StudyOnline.git (fetch)
origin  https://github.com/MahfuzKhandaker/StudyOnline.git (push)
Then you have to run the following command to remove origin:

git remote remove origin
And finally you have to add origin:

git remote  add origin  https://github.com/MahfuzKhandaker/StudyOnline.git
Then run the command:

git branch -M main
git push -u origin main
Hope this helps!

Share
Improve this answer
Follow
answered Oct 11, 2022 at 17:41
Mahfuz Khandaker's user avatar
Mahfuz Khandaker
41455 silver badges1111 bronze badges
Add a comment

0


You can see the multiple ways to solve but I recommended to trying this first. It works for me perfectly.

    step 1. git remote -v 
    step 2. git remote rm origin
    step 3. git add .
    step 4. git commit -m "your commit"
    step 5. git remote set-url origin https://github.com/<your_github_username>/<repository_name>.git
    step 6. git push --set-upstream -f origin main
Note: if error: No such remote 'origin' this error occurred. then before step 5 use this command -

git remote add origin https://github.com/<your_github_username>/<repository_name>.git
then again start from step 5

Follow this 6 steps, Thanks.

Share
Improve this answer
Follow
edited Mar 18 at 17:20
answered Mar 8 at 16:59
Md Wahiduzzaman Emon's user avatar
Md Wahiduzzaman Emon
59133 silver badges1010 bronze badges
Add a comment

0


you just need add github.com to your host file:

ssh-keygen -f "/home/<user>/.ssh/known_hosts" -R "github.com"
Share
Improve this answer
Follow
answered May 3 at 8:37
Jaber Alshami's user avatar
Jaber Alshami
33633 silver badges1414 bronze badges
Add a comment

-4


Sometimes you don't have a local REF for pushing that branch back to the origin.
Try

git push origin master:master
This explicitly indicates which branch to push to (and from)

Share
Improve this answer
Follow
answered Dec 13, 2018 at 13:25
vsriram92's user avatar
vsriram92
51811 gold badge44 silver badges1515 bronze badges
Add a comment
Highly active question. Earn 10 reputation (not counting the association bonus) in order to answer this question. The reputation requirement helps protect this question from spam and non-answer activity.

Not the answer you're looking for? Browse other questions tagged gitgithubversion-controlbranch or ask your own question.
The Overflow Blog
How to use marketing techniques to build a better resume
How the creator of Angular is dehydrating the web (Ep. 574)
Featured on Meta
AI/ML Tool examples part 3 - Title-Drafting Assistant
We are graduating the updated button styling for vote arrows
Temporary policy: ChatGPT is banned
Stack Overflow will be testing a title-drafting assistant, and we’d like your...
We are graduating the "Related questions using Machine Learning" experiment
The [connect] tag is being burninated
Linked
762
Updates were rejected because the tip of your current branch is behind its remote counterpart
2
Push on GIT and Bitbucket
0
Git - 'origin' does not appear to be a git repository
2
fatal: '~peterI/public_html/public.git' does not appear to be a git repository fatal: Could not read from remote repository
1
Local repository is not able to pull branch from remote repository
0
Change Git Username to Connect to My Remote Repo
2
Trying to pull from github i get error remote: Repository not found
1
I'm trying to do a git fetch. However, I'm receiving an error "remote: Repository not found. fatal: repository not found
0
error: failed to push some refs to 'git@github.com:MyGitHub/foo.git'
0
My project files are not getting pushed to GitHub repository
See more linked questions
Related
27
Git push origin master returns "fatal: No path specified."
0
Fatal error on git push origin master?
92
Git push error: "origin does not appear to be a git repository"
129
fatal: 'origin' does not appear to be a git repository
4
GIT: fatal: Could not read from remote repository when you create new branch
0
fatal: Could not read from remote repository error while git push
6
Git push origin Permission to * denied fatal: Could not read from remote repository
14
fatal- 'origin' does not appear to be a git repository
0
Git push origin master -f : "fatal 'origin' does not appear to be a git repository - fatal Could not read from remote repository."
1
Git push results in "Could not read from remote repository"
Hot Network Questions
Dovecot:/Thunderbird sslv3 alert certificate expired: SSL alert number 45
Should I pre-emptively confess after submitting work that was partially generated by ChatGPT?
What is \DocumentMetadata? What key-value pairs does it take and when should I use it?
How far apart has the sun drifted from Alpha Centari due to the expansion of the universe since its formation?
The Planet of the Ants: Giant Ant Physiology
Placing multiple nodes around a circle
Company wants to see offer letter received from another company to match salary
"Solvitas perambulum": Is this real Latin?
How many sorting networks?
What would be an example of something digital which isn't electronic?
Why did it take so long to invent telescopes given glass was used 4000 years ago in Mesopotamia?
Resultant of two polynomials
Why is Killiniq island divided between Nunavut and Labrador?
How can a passenger have opened an emergency exit on an Airbus A321 in flight?
Why did Trinity not take Neo to Morpheus when meeting him in the club?
How change the data arrangement in a list?
Is it appropriate to cite vulgar websites used for gathering data?
Did Nelson Mandela read The Economist in prison?
Can you pack these tetracubes to form a rectangular block with at least one odd side length?
Need help figuring out circuit board design
How to handle it if one player wants to take a risky course of action that nobody else wants?
Is there anything important to know about flying at ~9000ft for the first time?
Demarcated "Proof Idea"
Is Russian the most diverged Slavic language?
 Question feed

STACK OVERFLOW
Questions
Help
PRODUCTS
Teams
Advertising
Collectives
Talent
COMPANY
About
Press
Work Here
Legal
Privacy Policy
Terms of Service
Contact Us
Cookie Settings
Cookie Policy
STACK EXCHANGE NETWORK
Technology
Culture & recreation
Life & arts
Science
Professional
Business
API
DataHowever, at some point, I created a new branch locally called add-calendar-model in case next steps of the app development would go south...

... which is exactly what happened.

However, despite many attempts, I did not manage to get the initial code — i.e. the code from before I created the new branch — from the master branch to my local repository.

So, I decided to manually delete all the files from my local repository and git clone my master branch from GitHub.

This way, I got all my files back, but now, I cannot push any more to the remote repository.

Any time I try to run git push origin add-calendar-model or git push origin master, I get the following error:

fatal: 'origin' does not appear to be a git repository
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
I am not very comfortable with Git and GitHub, as you may have guessed by now, and I have to admit that I have no clue about how to fix this.

Any idea?

gitgithubversion-controlbranch
Share
Improve this question
Follow
asked Aug 27, 2015 at 0:03
Thibaud Clement's user avatar
Thibaud Clement
6,5271010 gold badges5050 silver badges103103 bronze badges
2
I had a similar error, But my problem was I had initialized git in the parent directory of the current folder I was trying it. Just in case if anyone is still facing, can look where the git is initialized and then try again. – 
Himanshu Kriplani
 Apr 17, 2020 at 2:39
Add a comment
17 Answers
Sorted by:

Highest score (default)

321


First, check that your origin is set by running

git remote -v
This should show you all of the push / fetch remotes for the project.

If this returns with no output, skip to last code block.

Verify remote name / address

If this returns showing that you have remotes set, check that the name of the remote matches the remote you are using in your commands.

$git remote -v
myOrigin ssh://git@example.com:1234/myRepo.git (fetch)
myOrigin ssh://git@example.com:1234/myRepo.git (push)

# this will fail because `origin` is not set
$git push origin main

# you need to use
$git push myOrigin main
If you want to rename the remote or change the remote's URL, you'll want to first remove the old remote, and then add the correct one.

Remove the old remote

$git remote remove myOrigin
Add missing remote

You can then add in the proper remote using

$git remote add origin ssh://git@example.com:1234/myRepo.git

# this will now work as expected
$git push origin main
Share
Improve this answer
Follow
edited Nov 4, 2021 at 20:14
Simo Pelle's user avatar
Simo Pelle
14111 silver badge1010 bronze badges
answered Aug 27, 2015 at 0:06
Matt Clark's user avatar
Matt Clark
27.6k1919 gold badges6767 silver badges122122 bronze badges
It worked for me without the ssh:// in front of git@example.com:1234/myRepo.git – 
Carol-Theodor Pelu
 Jul 16, 2018 at 7:05
I was reading this question if you could help with the new repository push error as well? – 
StaticVariable
 Sep 3, 2018 at 7:04
I renamed my remote branch from upstream to origin and it caused the error, after completely deleting the remote reference using git remote remove origin and then adding it again using git remote add origin <url> then it worked fine – 
Uriahs Victor
 Jun 29, 2021 at 18:31
This worked for me, with a slight tweak. git remote -v was showing that my origin was git@bitbucket.org/[repo].git. After removing that origin, I replaced it with just bitbucket.org/[repo].git, and this worked. To clarify, I got rid of the "git@" and just put in the repo URL without a user, prompting it to ask for a user for all push/pull commands (which is what I needed anyway). – 
Bad Programmer
 Aug 3, 2022 at 17:59
Add a comment

31


It works for me.

git remote add origin https://github.com/repo.git
git push origin master
add the repository URL to the origin in the local working directory

Share
Improve this answer
Follow
answered Jul 21, 2020 at 8:22
vinod's user avatar
vinod
52555 silver badges1010 bronze badges
2
When I removed the *.git in the end it worked for me: git remote add origin https://github.com/user/repo – 
Joel Wiklund
 Nov 5, 2022 at 7:12
Add a comment

16


As Matt Clark stated above

However, origin might not be set, so skip the deleting step and simply attempting to add can clear this up.

git remote add origin <"clone">
Where "clone" is simply going into your GitHub repo and copying the "HTTPS clone URL" and pasting into GitBash

Share
Improve this answer
Follow
answered Sep 21, 2015 at 16:38
heb-NR's user avatar
heb-NR
31755 silver badges1313 bronze badges
Add a comment

11


This is the way I updated the master branch

This kind of error occurs commonly after deleting the initial code on your project

So, go ahead, first of all, verify the actual remote version, then remove the origin add the comment, and copy the repo URL into the project files.

$ git remote -v
$ git remote rm origin
$ git commit -m "your commit"
$ git remote add origin https://github.com/user/repo.git
$ git push -f origin master
Share
Improve this answer
Follow
edited Dec 13, 2020 at 23:54
answered Jul 6, 2020 at 16:12
Jose Antonio's user avatar
Jose Antonio
8251414 silver badges2525 bronze badges
1
Try adding explanations to your answer in a way that addresses the question and attempts to help a reader understand. Currently, it just reads like some anecdote and wouldn't even work in the general case (e.g. https://github.com/ is the website root and a git repo) – 
Kache
 Jul 7, 2020 at 5:38
Add a comment

5


if you add your remote repository by using git clone then follow the steps:-

git clone <repo_url> then

git init

git add * *means add all files

git commit -m 'your commit'

git remote -v for check any branch run or not if not then nothing show then we add or fetch the repository. "fetch first". You need to run git pull origin <branch> or git pull -r origin <branch> before a next push.

then

git remote add origin <git url>
 git pull -r origin master
git push -u origin master```
Share
Improve this answer
Follow
answered May 13, 2020 at 11:49
md sha's user avatar
md sha
5111 silver badge11 bronze badge
Add a comment

3


Make sure the config file at .git is correct...Check URL & Make sure your using the correct protocol for your keys ...ProjectWorkspace/.git/config

  ~Wrong url for git@bitbucket
[core]
    repositoryformatversion = 0
    filemode = true
    bare = false
    logallrefupdates = true
[remote "origin"]
    url = gitbucket.org:Prezyack/project-one-hello.git
    fetch = +refs/heads/*:refs/remotes/origin/*

 ~Wrong URL for SSH...
[core]
    repositoryformatversion = 0
    filemode = true
    bare = false
    logallrefupdates = true
    ignorecase = true
    precomposeunicode = true
[remote "origin"]
    fetch = +refs/heads/*:refs/remotes/origin/*
    url = https://emmap1@bitbucket.org/emmap1/bitbucketspacestation.git
[branch "master"]
    remote = origin
    merge = refs/heads/master
We are looking at the URL... e.g: For bitbucket, expect git@bitbucket.org....If its gitbucket.org. make the necessary changes.. SAVE Try pushing again.

Share
Improve this answer
Follow
answered Jul 29, 2016 at 12:32
Magere's user avatar
Magere
9966 bronze badges
Add a comment

2


These two steps worked for me!

Step 1:

git remote set-url origin https://github.com/username/example_repo.git
Step 2:

git push --set-upstream -f origin main
Step 3:

your username and password for github

On step 2, -f is actually required because of the rebase, quote from this post.

Share
Improve this answer
Follow
answered Jan 21, 2021 at 13:07
BlueJapan's user avatar
BlueJapan
1,18622 gold badges1313 silver badges1616 bronze badges
Add a comment

2


For me it helps just by removing existing origin (after i created a new repo and few steps). But before check if the origin is exist in your case:

git remote -v
Then check name of origin (usually set by default) and remove it.

git remote remove origin
And use common github commands while pushing repository to add new origin and finally push your code:

git remote add origin https://github.com/username/repository.git
git branch -M main

git push -u origin main
Share
Improve this answer
Follow
edited Oct 17, 2022 at 8:09
answered Aug 5, 2022 at 9:40
user15038732
Add a comment

1


A similar error appears while pulling the changes from the origin. If you are trying in Intellij from the menu options, the pull might not work directly.

Go to terminal and type this command and this should work out: git pull origin master

Share
Improve this answer
Follow
answered Jun 13, 2018 at 7:50
Nikhil Shrivastav's user avatar
Nikhil Shrivastav
7111 silver badge22 bronze badges
Add a comment

1


What fixed this for me was re-setting my origin url:

git remote set-url origin https://github.com/username/example_repo.git

And then I was able to successfully git push my project. I had to do this even though when I viewed my origins with git remote -v, that the urls were same as what I re-set it as.

Share
Improve this answer
Follow
answered Nov 13, 2020 at 4:27
deesolie's user avatar
deesolie
81766 silver badges1717 bronze badges
Add a comment

1


Most probably the issue is that your remote origin is not set.

git add .
git commit -m "Your commit message"
git remote add origin https://repositoryurlpath.git
git push origin master
Extra Tips:

Check if the remote origin is set

git remote -v
Reset the remote origin

git remote remove origin
git remote add origin https://repositoryurlpath.git
Share
Improve this answer
Follow
answered Sep 14, 2021 at 19:26
Erielama's user avatar
Erielama
11111 silver badge33 bronze badges
Add a comment

0


I had the same issue. When I checked my config file I noticed that 'fetch = +refs/heads/:refs/remotes/origin/' was on the same line as 'url = Z:/GIT/REPOS/SEL.git' as shown:

[core]
    repositoryformatversion = 0
    filemode = false
    bare = false
    logallrefupdates = true
    symlinks = false
    ignorecase = true
[remote "origin"]
    url = Z:/GIT/REPOS/SEL.git     fetch = +refs/heads/*:refs/remotes/origin/*
[branch "master"]
    remote = origin
    merge = refs/heads/master
[gui]
    wmstate = normal
    geometry = 1109x563+32+32 216 255
At first I did not think that this would have mattered but after seeing the post by Magere I moved the line and that fixed the problem:

[core]
    repositoryformatversion = 0
    filemode = false
    bare = false
    logallrefupdates = true
    symlinks = false
    ignorecase = true
[remote "origin"]
    url = Z:/GIT/REPOS/SEL.git
    fetch = +refs/heads/*:refs/remotes/origin/*
[branch "master"]
    remote = origin
    merge = refs/heads/master
[gui]
    wmstate = normal
    geometry = 1109x563+32+32 216 255
Share
Improve this answer
Follow
answered Nov 21, 2019 at 21:05
Beaug45's user avatar
Beaug45
111 bronze badge
Add a comment

0


It happens when you push your code from the current location but after cloning any projects Git creates its own different folder so we have to change our current directory to the required directory. If any got these issue. We can solve it by following these easy steps:-

Firstly create an empty folder.
Open Git GUI/Bash or CMD in the empty folder. Open the empty folder and right click and then open Git.
Click on a clone in Bitbucket(after creating your repository) and copy the cloning path of your repository.
Paste it into your Git and Enter.
After cloning, a new folder is created by git.
Change your directory to the new folder that is created by Git after cloning your repository.
Paste/puts your desired projects/files/folder in this folder.
After keeping your all projects files. Again open Git GUI/Bash in the current folder.
Then type these as usual: a.git add --all b. git commit -m "Your Desired Heart Sound" c. git push -u origin master.
Finally after following these steps you push your projects to Bitbucket
Error:-fatal: Not a git repository (or any of the parent directories):

Thanks.

Share
Improve this answer
Follow
answered Feb 22, 2022 at 7:40
Naffy Kausar's user avatar
Naffy Kausar
8122 gold badges22 silver badges99 bronze badges
Add a comment

0


Firstly remote verbose with the following command:

git remote -v
And see the result of something like that:

origin  https://github.com/MahfuzKhandaker/StudyOnline.git (fetch)
origin  https://github.com/MahfuzKhandaker/StudyOnline.git (push)
Then you have to run the following command to remove origin:

git remote remove origin
And finally you have to add origin:

git remote  add origin  https://github.com/MahfuzKhandaker/StudyOnline.git
Then run the command:

git branch -M main
git push -u origin main
Hope this helps!

Share
Improve this answer
Follow
answered Oct 11, 2022 at 17:41
Mahfuz Khandaker's user avatar
Mahfuz Khandaker
41455 silver badges1111 bronze badges
Add a comment

0


You can see the multiple ways to solve but I recommended to trying this first. It works for me perfectly.

    step 1. git remote -v 
    step 2. git remote rm origin
    step 3. git add .
    step 4. git commit -m "your commit"
    step 5. git remote set-url origin https://github.com/<your_github_username>/<repository_name>.git
    step 6. git push --set-upstream -f origin main
Note: if error: No such remote 'origin' this error occurred. then before step 5 use this command -

git remote add origin https://github.com/<your_github_username>/<repository_name>.git
then again start from step 5

Follow this 6 steps, Thanks.

Share
Improve this answer
Follow
edited Mar 18 at 17:20
answered Mar 8 at 16:59
Md Wahiduzzaman Emon's user avatar
Md Wahiduzzaman Emon
59133 silver badges1010 bronze badges
Add a comment

0


you just need add github.com to your host file:

ssh-keygen -f "/home/<user>/.ssh/known_hosts" -R "github.com"
Share
Improve this answer
Follow
answered May 3 at 8:37
Jaber Alshami's user avatar
Jaber Alshami
33633 silver badges1414 bronze badges
Add a comment

-4


Sometimes you don't have a local REF for pushing that branch back to the origin.
Try

git push origin master:master
This explicitly indicates which branch to push to (and from)

Share
Improve this answer
Follow
answered Dec 13, 2018 at 13:25
vsriram92's user avatar
vsriram92
51811 gold badge44 silver badges1515 bronze badges
Add a comment
Highly active question. Earn 10 reputation (not counting the association bonus) in order to answer this question. The reputation requirement helps protect this question from spam and non-answer activity.

Not the answer you're looking for? Browse other questions tagged gitgithubversion-controlbranch or ask your own question.
The Overflow Blog
How to use marketing techniques to build a better resume
How the creator of Angular is dehydrating the web (Ep. 574)
Featured on Meta
AI/ML Tool examples part 3 - Title-Drafting Assistant
We are graduating the updated button styling for vote arrows
Temporary policy: ChatGPT is banned
Stack Overflow will be testing a title-drafting assistant, and we’d like your...
We are graduating the "Related questions using Machine Learning" experiment
The [connect] tag is being burninated
Linked
762
Updates were rejected because the tip of your current branch is behind its remote counterpart
2
Push on GIT and Bitbucket
0
Git - 'origin' does not appear to be a git repository
2
fatal: '~peterI/public_html/public.git' does not appear to be a git repository fatal: Could not read from remote repository
1
Local repository is not able to pull branch from remote repository
0
Change Git Username to Connect to My Remote Repo
2
Trying to pull from github i get error remote: Repository not found
1
I'm trying to do a git fetch. However, I'm receiving an error "remote: Repository not found. fatal: repository not found
0
error: failed to push some refs to 'git@github.com:MyGitHub/foo.git'
0
My project files are not getting pushed to GitHub repository
See more linked questions
Related
27
Git push origin master returns "fatal: No path specified."
0
Fatal error on git push origin master?
92
Git push error: "origin does not appear to be a git repository"
129
fatal: 'origin' does not appear to be a git repository
4
GIT: fatal: Could not read from remote repository when you create new branch
0
fatal: Could not read from remote repository error while git push
6
Git push origin Permission to * denied fatal: Could not read from remote repository
14
fatal- 'origin' does not appear to be a git repository
0
Git push origin master -f : "fatal 'origin' does not appear to be a git repository - fatal Could not read from remote repository."
1
Git push results in "Could not read from remote repository"
Hot Network Questions
Dovecot:/Thunderbird sslv3 alert certificate expired: SSL alert number 45
Should I pre-emptively confess after submitting work that was partially generated by ChatGPT?
What is \DocumentMetadata? What key-value pairs does it take and when should I use it?
How far apart has the sun drifted from Alpha Centari due to the expansion of the universe since its formation?
The Planet of the Ants: Giant Ant Physiology
Placing multiple nodes around a circle
Company wants to see offer letter received from another company to match salary
"Solvitas perambulum": Is this real Latin?
How many sorting networks?
What would be an example of something digital which isn't electronic?
Why did it take so long to invent telescopes given glass was used 4000 years ago in Mesopotamia?
Resultant of two polynomials
Why is Killiniq island divided between Nunavut and Labrador?
How can a passenger have opened an emergency exit on an Airbus A321 in flight?
Why did Trinity not take Neo to Morpheus when meeting him in the club?
How change the data arrangement in a list?
Is it appropriate to cite vulgar websites used for gathering data?
Did Nelson Mandela read The Economist in prison?
Can you pack these tetracubes to form a rectangular block with at least one odd side length?
Need help figuring out circuit board design
How to handle it if one player wants to take a risky course of action that nobody else wants?
Is there anything important to know about flying at ~9000ft for the first time?
Demarcated "Proof Idea"
Is Russian the most diverged Slavic language?
 Question feed

STACK OVERFLOW
Questions
Help
PRODUCTS
Teams
Advertising
Collectives
Talent
COMPANY
About
Press
Work Here
Legal
Privacy Policy
Terms of Service
Contact Us
Cookie Settings
Cookie Policy
STACK EXCHANGE NETWORK
Technology
Culture & recreation
Life & arts
Science
Professional
Business
API
Data
