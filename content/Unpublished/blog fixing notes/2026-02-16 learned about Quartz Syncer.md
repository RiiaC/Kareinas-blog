# the question that started the conversation 
- on [[2026-02-16 grateful I took today off|2026-02-16]] I asked on the [Quartz Discord channel](https://discord.com/channels/927628110009098281/927628110009098284/1472945236509589587):
> I currently have Obsidian sync on my phone set to ignore my Quartz and githup folders of my vault, so that it will open reasonably quickly. These days I do most of my writing on the phone, and find it bothersome to have to go to a computer to push to Github to update the web version of my vault.
> Do any of you who also work mostly on a phone have a good system for getting your vault pushed to Github and published that doesn't make opening the vault on the phone take too long?
# [the first reply, from arden13,](https://discord.com/channels/927628110009098281/927628110009098284/1472946353175789731) said:

Could you make a little background shell script that monitors the folder for changes and pushes for you?
I tend to keep my vault separated from my quartz repo, though still in a (separate) git repo. The quartz build is then a more complicated dockerfile that clones the content, builds the quartz site, and returns the built content and runs it
## [the second reply, from saberzero1,](https://discord.com/channels/927628110009098281/927628110009098284/1472955688572682382) said:
Just use the Quartz Syncer plugin in Obsidian.
You don't have to have Quartz as part of your vault with that, just the notes you want to publish to Quartz.
https://obsidian.md/plugins?id=quartz-syncer
Plugins are lazy-loaded nowadays. Shouldn't affect startup time.
- [DoghouseMike seconded](https://discord.com/channels/927628110009098281/927628110009098284/1473062392769548380):
Yea, give the syncer plugin a go. Worst case scenario, it *does* slow down the launch a bit, if it's too much, delete it. 5-10 minutes work might save you a pile more time delving into more complex solutions. 
FWIW it doesn't seem to slow mine down. Vid from iPhone 13 mini for reference.
# my replies to [the first reply](https://discord.com/channels/927628110009098281/927628110009098284/1472946353175789731):
> Do you have a more comprehensive set of instructions or workflow for that? I am certainly not good enough at computer stuff, yet, to have any understanding of how one might accomplish that just from your summary.
- to which **arden13** said:
> Ah fair. It's on my work laptop so I can't today, but (from memory, don't trust the syntax!) the workflow in the dockerfile is something like
```From alpine-git as clone_1
workdir /usr/content
Git clone content repo 

From alpine-git as clone_2
Workdir /usr/src/app
Git clone <replace with quartz for repo>

FROM node:22-slim AS builder
WORKDIR /usr/src/app
Copy --from=clone_2 /usr/src/app /usr/src/app
Copy --from=clone_1 /usr/content/<repo_name> /usr/src/app/quartz/content
COPY package.json .
COPY package-lock.json* .
RUN npm ci

FROM node:22-slim
WORKDIR /usr/src/app
COPY --from=builder /usr/src/app/ /usr/src/app/
COPY . .
CMD ["npx", "quartz", "build", "--serve"]
````
> The workflow is to clone the two repositories, content and app, then build them. The details I can all but guarantee you are wrong, I am still a novice with docker and it's folder structures
> That being said, this may not be fully answering your need. It seems you want your laptop to automatically detect content changes from your phone and then push to a website.
> This workflow with docker still requires your content to be pushed to a repository and the workflow to be started from your app-building repo.
- to which I replied:
> What I want is a way to skip the laptop. Just publish from the phone. However, I don't want to pay the price of a slow start up time in Obsidian to accomplish this.
- to which **arden13** replied:
> Yep. My method won't fix that for you off the cuff, you still need some sort of service running on your laptop
> I'm not familiar with <@122650623500877826> 's recommendation of quartz sync, perhaps something to explore
- on [[2026-02-18 it was a good bowl]] I went back [and replied](https://discord.com/channels/927628110009098281/927628110009098284/1473470716249637124):
>I just woke up thinking about the part where you keep your vault separate from your Quartz repro, and I would love to learn more about that. While I appreciate being able to use Quartz to transform my vault into my GitHub pages blog, I have never cared for the price of a "messy" vault with all those extra folders that come with Quartz. I miss being able to push the "collapse all folders" button in Obsidian and seeing only my own top level folders.

# [my response](https://discord.com/channels/927628110009098281/927628110009098284/1473193213031612446) to [the second reply, from  **saberzero1**.](https://discord.com/channels/927628110009098281/927628110009098284/1472955688572682382) 
Ok, now I have had a chance to read the quartz syncer documentation, and if I am understanding it correctly, since I already have quartz working with GitHub pages, all I need to do to make it work to publish from my phone is:
1. use a bulk property adding plugin to add a publish property to everything in the folders that are currently published (right now it is everything in the "content" folder)
2. add the "publish"n property to all of my current templates so that future notes will also have it
3. add the quartz syncer plug in
4. run it
it should work. 
Can anyone confirm or deny my understanding, and add any points I may have missed?
- to which  **saberzero1** replied:
> If you have all notes that you want to publish in a single folder, you can configure that as the root in Quartz Syncer.
> Outside of that, pretty much on point.
- and  **DoghouseMike** replied:
> What Saberzero said!
> I'd add that if you set "Publish" as TRUE in your templates, you'll end up publishing them too (unless you're excluding that folder). So unless that's intended, I'd either add the folder where your templates live to the ```.gitignore ``` file (in your GitHub repo), or have the templates set up so they have the Publish property set to FALSE by default.
> I must admit I am perhaps slightly paranoid about unintentionally publishing the wrong thing(s) 🤣
- on [[2026-02-18 it was a good bowl]] I went back [and replied](https://discord.com/channels/927628110009098281/927628110009098284/1473475618812461239):
> The part where you don't have to have Quartz as part of your vault with Quartz Syncer is very appealing. For those of us who didn't know that would be possible, and aready do, is there a recommend workflow, including the best order in which to extract Quartz from the vault and get Quartz syncer working with the vault for publishing to a GitHub pages blog?
> How about advice for those of us with multiple Github pages  blogs from multiple vaults? If we extract Quartz from those vaults and use Quartz Syncer to publish them, do we still need multiple copies of Quartz anymore, or is there a more efficient setup that would permit one Quartz folder on the computer, containing sub folders with the different quartzconfig etc files needed for each vault/blog?
- to which **saberzero1** replied:
> If you have multiple vaults, just configure Quartz Syncer per vault.
[- to which I replied:](https://discordapp.com/channels/927628110009098281/927628110009098284/1473580117799206943)
> Thanks!  The Quartz Syncer documentation says "This plugin manages Quartz content from Obsidian. Please set up Quartz on your Git provider before continuing." and above you say* "You don't have to have Quartz as part of your vault with that, just the notes you want to publish to Quartz."* 
> I currently have Quartz set up on my Git provider. However, right now I have one full copy of Quartz in each Obsidian vault that I am publishing. If I understand you correctly, I should be able to take all of the Quartz and GitHub folders out of my Obsidian vaults, put one copy of them Somewhere Else and then set up Quartz Syncer for each vault to use Quartz to publish to my GitHub pages blogs. Is that correct?
> If so, where should that Somewhere Else be in order for this to work for publishing from either my phone or my computer? Is it enough to use my computer to set up an additional GitHub repro containing Quartz, and then tell Quartz Syncer where it is located?
> If I am doing this change, do you recommend first stripping Quartz out of the Obsidian Vaults and setting up its new location, before introducing Quartz Syncer into the mix?
> (sorry for having so many questions, but it took a while to get Quartz working to publish my blogs in the first place, and thus I am afraid to break it while trying to improve how I use it, and so want to be absolutly certain I understand what I should do before I try doing it)
- [to which **saberzero1** replied](https://discordapp.com/channels/927628110009098281/927628110009098284/1473633359933476966):
> Easiest would be to move every Quartz to a place outside your vault, then move the files in the `content` folder back into your vault. Make sure to check for hidden files (there should be a `.git` and possibly a `.quartz` folder.) Do this for every vault with Quartz. Quartz Syncer automatically manage your Quartz repository inside Obsidian's storage. Technically twice, one local copy and one remote copy. Quartz Syncer processes your notes, copies them to the local copy, updates the remote copy, compares them (this is what is used in the diff views) and applies your changes to the remote copy if you hit publish. This last part is similar to running `npx quartz sync`. After Quartz v5 is released, I'll update Quartz Syncer to be able to fully manage Quartz, including configuring, updating, and installing plugins.
# how to set up Quartz Syncer 
- On [[2026-02-19 quiet day]] **DoghouseMike** posted in reply to the above thread:
> Dunno if still useful, but threw this together [https://doghouse-mike.github.io/Bin-me/Setting-up-Quartz-From-Scratch-using-Syncer](https://doghouse-mike.github.io/Bin-me/Setting-up-Quartz-From-Scratch-using-Syncer "https://doghouse-mike.github.io/Bin-me/Setting-up-Quartz-From-Scratch-using-Syncer")
- to which I replied
> Thanks!  I have a question for clarity. In step 2 of Set Up Quartz Syncer, the remote URL we assign, that is pointing specifically to the Quartz repository that is created in the first step, and the repository name to be used there will be name assigned to the Quartz repository?  Which will also become the name of the blog if using that repository to make a GitHub Pages blog?If so, that implies for me that we would need a separate Quartz repository in GitHub for every Obsidian Vault we publish to a web page. Is that correct? Or is there a way in Quartz Syncer to go through one repository to different blogs, with different names where the repository name normally  sits in the remote URL? 
- to which **saberzero1** replied:
> Yes. You need a repository per GitHub Pages site.
- and **DoghouseMike** replied:
> Yea, what he said ![😅](https://discordapp.com/assets/5134d215343b97ef.svg) If you’re running multiple vaults though, the plugin would/should be set up to point to different reposb (In each vault)
> To which I replied:
> Great, thanks both of you, I really appreciate your taking the time to help me with all of my questions. So, since I already have repos set up for each vault, and they are already publishing to my blogs, I should be able to add quartz syncer without changing anything, just point to the existing repos. That sounds great.
> However, the part about taking the quartz stuff out of the vault on my phone and desktop and having it only in the repo sounds appealing. Are there any tips or tricks you can recommend to do that without breaking anything? I would hate to take it out of the vault, on the computer/phone and have the quartz/github essential stuff also disappear from the repository.
> Oh, and if I did that, how would I then go about editing things like quartzconfig if I decided to change something? Is it better to just leave that stuff in the vault?


Months later, I finally tried, first getting it working for SEAD structure, than having enough problems with the personal blog, that my to-do list stalled ([[Unpublished/blog fixing notes/2026-07-27 migrating to Quartz Sync]]) and I opened a "Me too" comment at https://github.com/saberzero1/quartz-syncer/issues/134